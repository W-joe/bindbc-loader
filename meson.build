## Build file for meson

project('bindbc-loader', 'd',
	meson_version: '>=0.46.0',
	license: 'Boost',
	version: '0.2.1',
	subproject_dir: 'subprojects',
	default_options: [
		'buildtype=release',
		],
	)

project_name		= meson.project_name()
project_target		= project_name + '_' + meson.get_compiler('d').get_id()
project_description	= 'Cross-platform shared library loader and a number of utility modules used by the bincbc libraries.'
project_homepage	= 'https://github.com/BindBC/bindbc-loader'


## Import directories
import_dir = include_directories(
	'source/',
	)

## Source Files
source_files = [
	'source/bindbc/loader/package.d',
	'source/bindbc/loader/sharedlib.d',
	'source/bindbc/loader/system.d',
	]


## Target
target_lib = static_library(
	project_target,
	sources: source_files,
	include_directories: import_dir,
	install: true,
	pic: true,
	)

install_subdir('source/bindbc/', install_dir: 'include/d/')


## Dependency
bindbc_loader_dep = declare_dependency(
	include_directories: import_dir,
	link_with: target_lib,
	version: meson.project_version(),
	)


## pkg-config
pkgConf = import('pkgconfig')
pkgConf.generate(
	name: project_target,
	libraries: target_lib,
	subdirs: 'd/',
	version: meson.project_version(),
	description: project_description,
	)

