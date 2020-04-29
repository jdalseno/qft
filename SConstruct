import os

env = Environment(ENV=os.environ)

# Set up compilation environment
env.Append(CPPPATH = ['#include'])
#env.Append(CXXFLAGS = ['-O3', '-Wall', '-Wextra', '-pedantic',  '-Werror', '-std=c++14'])
env.Append(CXXFLAGS = ['-O3', '-Wall', '-Wextra', '-pedantic', '-std=c++17'])
#env.Append(CXXFLAGS = ['-O3', '-Wall', '-Wextra', '-pedantic',  '-Werror'])

#Export environment
Export('env')

#Run SConscript files
SConscript('SConscript')

# Set up installation environment
AddOption('--install',
	  dest='install',
          type='string',
          nargs=1,
          action='store',
          metavar='DIR',
          help='Installation directory')

install = GetOption('install')

if install != None:
   if os.path.isfile('lib/libqft++.so') is False:
      print('\033[91m' 'ERROR: ' '\033[0m' 'qft++ needs to be built first')
      quit()
   if not os.path.exists(install):
       os.makedirs(install)
   os.system('cp -r include ' + install)
   os.system('cp -r src ' + install)
   os.system('cp -r lib ' + install)
   os.system('rm -f ' + install + '/src/SConscript')
   os.system('rm -f ' + install + '/src/*/SConscript')
   print('Installation complete')
