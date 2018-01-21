####  关于搭建的流程
* 创建仓库:chamzheng.github.io;
* 创建两个分支:'master'与'hexo';
* 设置hexo为默认分支(因为我们只需要手动管理这个分支上的Hexo网站文件);
* 使用git clone git@github.com:chamzheng/chamzheng.github.io.git拷贝仓库；
* 在本地chamzheng.github.io文件夹下通过Git bash依次执行npm install hexo、hexo init、npm install 和 npm install hexo-deployer-git（此时当前分支应显示为hexo);
* 修改_config.yml中的deploy参数，分支应为master；
* 依次执行git add ., git commit -m "...", git push origin hexo提交网站相关的文件；
* 执行hexo g -d生成网站并部署到GitHub上。这样一来，在GitHub上的http://chamzheng.github.io.git 仓库就有两个分支，一个hexo分支用来存放网站的原始文件，一个master分支用来存放生成的静态网页。完美( •̀ ω •́ )y！
#### 关于日常的改动流程在本地对博客进行修改（添加新博文、修改样式等等）后，通过下面的流程进行管理。
* 依次执行git add ., git commit -m "...", git push origin hexo指令将改动推送到GitHub（此时当前分支应为hexo）；
* 然后才执行hexo g -d发布网站到master分支上。虽然两个过程顺序调转一般不会有问题，不过逻辑上这样的顺序是绝对没问题的（例如突然死机要重装了，悲催....的情况，调转顺序就有问题了）。
#### 本地资料丢失后的流程当重装电脑之后，或者想在其他电脑上修改博客，可以使用下列步骤：
* 使用git clone git@github.com:chamzheng/chamzheng.github.io.git拷贝仓库（默认分支为hexo）；
* 在本地新拷贝的http://chamzheng.github.io.git 文件夹下通过Git bash依次执行下列指令：npm install hexo、npm install、npm install hexo-deployer-git（记得，不需要hexo init这条指令）。