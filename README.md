# Biorthogonal-curvature-Python-code
# Code for CASE TS^2
import numpy as np

import scipy . optimize as opt

# Fixed parameters

c = 20

KS2 = 50

# Function f1 and its derivatives ( for S ^2)

def f1 ( theta , phi ) :

return c * np . sin ( theta ) * np . cos ( phi )

def grad_f1_squared ( theta , phi ) :

return c **2 * ( np . cos ( theta ) **2 * np . cos ( phi ) **2 +

np . sin ( phi ) **2)

def hess_f1 ( theta , phi ) :

return c * np . cos ( phi ) * ( np . cos ( theta ) **2 - 2 *

np . sin ( theta ) )

# Biorthogonal curvature function for TS ^2 planes

def K_biort_TS2 ( vars ) :

theta , phi = vars

f1_val = f1 ( theta , phi )

grad_sq = grad_f1_squared ( theta , phi )

hess_val = hess_f1 ( theta , phi )

return 0.5 * np . exp ( -2 * f1_val ) * ( KS2 - hess_val

+ grad_sq )

# Optimization bounds

bounds_TS2 = [(0 , np . pi ) , (0 , 2 * np . pi ) ]

# Global optimization with Differential Evolution

result_de_TS2 = opt . differential_evolution ( K_biort_TS2

, bounds_TS2 , strategy = ’ best1bin ’ , tol =1 e -12 ,

maxiter =1000 , seed =42)

# Print final results

print ( " K_biort ␣ minimum :" , result_de_TS2 . fun )
