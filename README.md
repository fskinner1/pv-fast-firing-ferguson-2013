# pv-fast-firing-ferguson-2013
'''
PV cell model
@author: Ferguson et al. (2013) Front. Comput. Neurosci.
'''
from brian import *

defaultclock.dt = 0.02*ms

#PV cell parameters
C=90 * pF
vr=-60.6 * mV
vpeak=2.5 * mV
c=-70 * mV
klow=1.7 * nS/mV
khigh=14  * nS/mV
a=0.1 /ms
d=0.1 * pA
vt=-43.1 *mV
b=-0.1 * nS

N=1   #number of cells
mean_Iapp=150 #mean Iapplied input

time=0

#cell eqns
pv_eqs = """
Iext  : amp
k=(v<vt)*klow+(v>=vt)*khigh : (siemens/volt)
du/dt = a*(b*(v-vr)-u)            : amp
dv/dt = (k*(v-vr)*(v-vt)+Iext -u)/C : volt
"""
