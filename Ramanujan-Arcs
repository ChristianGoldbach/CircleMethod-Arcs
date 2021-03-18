# Code from https://titanwolf.org/Network/Articles/Article?AID=756e0d78-e4ef-400a-a157-9bf4af6741ee#gsc.tab=0

from fractions import Fraction
 
 
class Fr(Fraction):
    def __repr__(self):
        return '(%s/%s)' % (self.numerator, self.denominator)
 
 
def farey(n, length=False):
    if not length:
        return [Fr(0, 1)] + sorted({Fr(m, k) for k in range(1, n+1) for m in range(1, k+1)})
    else:
        #return 1         +    len({Fr(m, k) for k in range(1, n+1) for m in range(1, k+1)})
        return  (n*(n+3))//2 - sum(farey(n//k, True) for k in range(2, n+1))
 
if __name__ == '__main__':
    print('Farey sequence for order 1 through 11 (inclusive):')
    for n in range(1, 12): 
        print(farey(n))
        
# Our work

import numpy as np

intervalos = []
for i in range(0,len(farey(9))):
    if i == 0:
        pass
    elif i == len(farey(9))-1:
        pass
    else:
        intervalo = (farey(9)[i] - 1/(farey(9)[i].denominator*(farey(9)[i].denominator + farey(9)[i-1].denominator)), farey(9)[i] + 1/(farey(9)[i].denominator*(farey(9)[i].denominator + farey(9)[i+1].denominator)))
        intervalos.append(intervalo)
for i in np.linspace(intervalos[0][0], intervalos[0][1], 50):
    print(i)
nueva = np.linspace(intervalos[0][0], intervalos[0][1], 50)

x = []
y = []

for i in nueva:
    coseno = np.cos(2*np.pi*i)
    seno = np.sin(2*np.pi*i)
    x.append(coseno)
    y.append(seno)
    
import matplotlib
import matplotlib.pyplot as plt

plt.gca().set_aspect('equal', adjustable='box')
plt.rcParams["figure.figsize"] = (10,10)
plt.scatter(x,y)

for i in range(0, len(farey(9))-2):
    globals()['x' + str(i)] = []
    globals()['y' + str(i)] = []
    nueva = np.linspace(intervalos[i][0], intervalos[i][1], 50)
    for j in nueva:
        coseno = np.cos(2*np.pi*j)
        seno = np.sin(2*np.pi*j)
        globals()['x' + str(i)].append(coseno)
        globals()['y' + str(i)].append(seno)
        
plt.gca().set_aspect('equal', adjustable='box')
plt.rcParams["figure.figsize"] = (10,10)
for i in range(0, len(farey(9))-2): 
    plt.scatter(globals()['x' + str(i)], globals()['y' + str(i)])
plt.savefig('hola.eps')
