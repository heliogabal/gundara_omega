'use strict';
module.exports = function (grunt) {
  grunt.loadNpmTasks('grunt-contrib-watch');
  grunt.loadNpmTasks('grunt-contrib-compass');
  grunt.loadNpmTasks('grunt-contrib-sass');
  grunt.loadNpmTasks("grunt-autoprefixer");
  grunt.loadNpmTasks('grunt-contrib-jshint');
  grunt.loadNpmTasks('grunt-contrib-uglify');
  grunt.loadNpmTasks('grunt-shell');
  grunt.initConfig({
    watch: {
      options: {
        livereload: true
      },
      sass: {
        files: ['sass/{,**/}*.{scss,sass}'],
        //tasks: ['compass:dev'],
        tasks: ['sass:styles']
      },
      registry: {
        files: ['*.info', '{,**}/*.{php,inc}'],
        tasks: ['shell'],
        options: {
          livereload: false
        }
      },
      images: {
        files: ['images/**']
      },
      css: {
        files: ['css/{,**/}*.css']
      },
      js: {
        files: ['js/{,**/}*.js', '!js/{,**/}*.min.js'],
        tasks: ['jshint', 'uglify:dev']
      }
    },
    shell: {
      all: {
        command: 'drush cache-clear theme-registry'
      }
    },
    sass: {
      options: {
        bundleExec: true,
        compass: true,
        require: [
          'compass',
          'breakpoint',
          'susy',
          'sassy-maps',
          'sass-globbing',
        ]
      },
      dist: {
        options: {
          style: 'compressed',
          //sourcemap: false
        },
        files: [{
          expand: true,
          cwd: 'sass',
          src: ['*.scss'],
          dest: 'css',
          ext: '.css'
        }]
      },
      dev: {
        options: {
          style: 'nested',
          sourcemap: true
        },
        files: [{
          expand: true,
          cwd: 'sass',
          src: ['*.scss'],
          dest: 'css',
          rename: function(dest, src) {
            var folder = src.substring(0, src.lastIndexOf('/'));
            var filename = src.substring(src.lastIndexOf('/'), src.length);
            filename = filename.substring(0, filename.lastIndexOf('.'));
            return dest + '/' + folder + filename + '.css';
          }
        }],
      },
      styles: {
        options: {
          style: 'nested',
          sourcemap: true
        },
        files: {
          'css/omega-custom.styles.css': 'sass/omega-custom.styles.scss'
        }
      }
    },
    compass: {
      options: {
        //config: 'config.rb', //not needed anymore
        sassDir: 'sass',
        cssDir: 'css',
        imagesDir: 'images',
        javascriptsDir: 'js',
        bundleExec: true,
        relativeAssets: true,
        require: [
          'breakpoint',
          'singularitygs',
          'sassy-maps',
          'sass-globbing',
        ],
        force: true, //allows compass to override existing files
      },
      dev: {
        options: {
          environment: 'development',
          sourcemap: true,
          noLineComments: true,
          outputStyle: 'nested',
        }
      },
      dist: {
        options: {
          environment: 'production',
        }
      }
    },
    autoprefixer: {
      options: {
        browsers: ["last 2 version", "> 1%", "Firefox ESR", "Opera 12.1", "Explorer 5", "Android 2"]
      },
      dist: {
        expand: true, // Enable dynamic expansion. (en gros permet d'utiliser les options ci-dessous)
        flatten: true, //Remove all path parts from generated dest paths (??)
        cwd: "./css",
        src: ["*.css"],
        dest: "./css/",
      }
    },
    jshint: {
      options: {
        jshintrc: '.jshintrc'
      },
      all: ['js/{,**/}*.js', '!js/{,**/}*.min.js']
    },
    uglify: {
      dev: {
        options: {
          mangle: false,
          compress: false,
          beautify: true
        },
        files: [{
          expand: true,
          flatten: true,
          cwd: 'js',
          dest: 'js',
          src: ['**/*.js', '!**/*.min.js'],
          rename: function(dest, src) {
            var folder = src.substring(0, src.lastIndexOf('/'));
            var filename = src.substring(src.lastIndexOf('/'), src.length);
            filename = filename.substring(0, filename.lastIndexOf('.'));
            return dest + '/' + folder + filename + '.min.js';
          }
        }]
      },
      dist: {
        options: {
          mangle: true,
          compress: true
        },
        files: [{
          expand: true,
          flatten: true,
          cwd: 'js',
          dest: 'js',
          src: ['**/*.js', '!**/*.min.js'],
          rename: function(dest, src) {
            var folder = src.substring(0, src.lastIndexOf('/'));
            var filename = src.substring(src.lastIndexOf('/'), src.length);
            filename = filename.substring(0, filename.lastIndexOf('.'));
            return dest + '/' + folder + filename + '.min.js';
          }
        }]
      }
    }
  });
  grunt.registerTask('build', [
    'uglify:dist',
    //'compass:dist',
    'sass:dist',
    'autoprefixer',
    'jshint'
  ]);
};
