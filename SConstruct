import os

env = Environment(ENV=os.environ)

# Set up compilation environment
env.Append(CPPPATH = ['#include'])
env.Append(CXXFLAGS = ['-O3', '-Wall', '-pedantic',  '-Werror', '-std=c++11'])
env.Append(LIBPATH = ['/home/jdalseno/qft++_test'])

#Export environment
Export('env')

#Run SConscript files
SConscript('SConscript')

# Set up installation environment
AddOption('--prefix',
	  dest='prefix',
          type='string',
          nargs=1,
          action='store',
          metavar='DIR',
          help='installation prefix')

install = GetOption('prefix')

if install != None:
   if not os.path.exists(install):
       os.makedirs(install)
   os.system('cp -r include ' + install)
   os.system('cp -r src ' + install)
   os.system('cp -r lib ' + install)
   os.system('rm -f ' + install + '/src/SConscript')
   os.system('rm -f ' + install + '/src/*/SConscript')

