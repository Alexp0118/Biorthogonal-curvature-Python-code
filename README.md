# Biorthogonal-curvature-Python-code
# CODE FOR CASE TS^2
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


# CODE FOR CASE TT^2
import numpy as np
import scipy . optimize as opt
# Fixed parameters
a = 5
b = 2
# Function f2 and its derivatives ( for T ^2)
def f2 ( y1 , y2 ) :
return a * y1 + b * ( np . sin ( y1 ) **2 + np . cos ( y2 )
**2)
def grad_f2_squared ( y1 , y2 ) :
return ( a + 2 * b * np . sin ( y1 ) * np . cos ( y1 ) ) **2 +
(2 * b * np . sin ( y2 ) * np . cos ( y2 )) **2
def hess_f2 ( y1 , y2 ) :
return 2 * b * ( np . cos (2 * y1 ) + np . cos (2 * y2 ) )
# Biorthogonal curvature function for TT ^2 planes
def K_biort_TT2 ( vars ) :
y1 , y2 = vars
f2_val = f2 ( y1 , y2 )
grad_sq = grad_f2_squared ( y1 , y2 )
hess_val = hess_f2 (y1 , y2 )
return 0.5 * np . exp ( -2 * f2_val ) * ( - hess_val +
grad_sq )
# Optimization bounds
bounds_TT2 = [(0 , 2 * np . pi ) , (0 , 2 * np . pi ) ]
# Global optimization with Differential Evolution

result_de_TT2 = opt . differential_evolution ( K_biort_TT2

, bounds_TT2 , strategy = ’ best1bin ’ , tol =1 e -12 ,

maxiter =1000 , seed =42)

# Print final results

print ( " K_biort ␣ minimum :" , result_de_TT2 . fun )

# CODE FOR CASE MIXED PLANES
import numpy as np
import scipy . optimize as opt
# Fixed parameters

c = 20

a = 5

b = 2

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

# Function f2 and its derivatives ( for T ^2)

def f2 ( y1 , y2 ) :

return a * y1 + b * ( np . sin ( y1 ) **2 + np . cos ( y2 )

**2)

def grad_f2_squared ( y1 , y2 ) :

return ( a + 2 * b * np . sin ( y1 ) * np . cos ( y1 ) ) **2 +

(2 * b * np . sin ( y2 ) * np . cos ( y2 )) **2

def hess_f2 ( y1 , y2 ) :

return 2 * b * ( np . cos (2 * y1 ) + np . cos (2 * y2 ) )

# Biorthogonal curvature for mixed planes

def K_biort_mixed ( vars ) :

theta , phi , y1 , y2 = vars

# function value

f1_val = f1 ( theta , phi )

f2_val = f2 ( y1 , y2 )

# Gradient

grad_f1_sq = grad_f1_squared ( theta , phi )
grad_f2_sq = grad_f2_squared ( y1 , y2 )

# Hessian for mixed planes

hess_f1_v = hess_f1 ( theta , phi )

hess_f1_v_ortho = hess_f1 ( theta + np . pi / 2, phi )

hess_f2_w = hess_f2 ( y1 , y2 )

hess_f2_w_ortho = hess_f2 ( y1 + np . pi / 2 , y2 )

# Biorthogonal curvature

return 0.5 * np . exp ( -2 * ( f1_val + f2_val )) * (

2 * KS2 + grad_f1_sq + grad_f2_sq - hess_f1_v

- hess_f1_v_ortho - hess_f2_w -

hess_f2_w_ortho

)

# research domain

bounds = [(0 , np . pi ) , (0 , 2 * np . pi ) , (0 , 2 * np . pi ) ,

(0 , 2 * np . pi ) ]

# Global otimization with Differential Evolution

result_de = opt . differential_evolution ( K_biort_mixed ,

bounds , strategy = ’ best1bin ’, tol =1 e -12 , maxiter

=1000 , seed =42)

# Print final results

print ( " K_biort ␣ minimum :" , result_de . fun )

