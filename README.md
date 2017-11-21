# tool-gulpcsswrap [批量给css文件增加命名空间]
# 说明：

使用的是npm包[gulp-css-wrap](https://npm.taobao.org/package/gulp-css-wrap)

[gulp使用指南](http://www.gulpjs.com.cn/docs/getting-started/)

如我们给css文件的每个加上.custom-1b1e24类名

原css文件：

.header{height:100px;}

.content{color:#fff;}

=>输出 

.custom-1b1e24 .header{height:100px;}

.custom-1b1e24 .content{color:#fff;}

# 运行：
npm install

gulp css-wrap

# P.S.

如果要换存放目录或者修改前缀则只需修改根目录下的gulpfile.js 文件即可

```
var path = require('path')
var gulp = require('gulp')
var cleanCSS = require('gulp-clean-css')
var cssWrap = require('gulp-css-wrap')
gulp.task('css-wrap', function () {
	return gulp.src(path.resolve('./theme/index.css'))/* 找需要添加命名空间的css文件，支持正则表达式 */
		.pipe(cssWrap({
			selector: '.custom-1b1e24' /* 添加的命名空间 */
		}))
		.pipe(cleanCSS())
		.pipe(gulp.dest('assets/theme/1b1e24')) /* 存放的目录 */
})
```

