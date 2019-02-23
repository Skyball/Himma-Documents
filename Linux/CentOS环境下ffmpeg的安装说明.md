### CentOS环境下ffmpeg的安装说明:

#### 1.安装gcc cc cl

```
yum -y install gcc cc cl
```

#### 2.安装yasm

```
wget http://www.tortall.net/projects/yasm/releases/yasm-1.3.0.tar.gz
tar -zxvf yasm-1.3.0.tar.gz
cd yasm-1.3.0/
./configure && make && make install
```

#### 3.安装ffmpeg

```
wget http://www.ffmpeg.org/releases/ffmpeg-4.1.tar.gz
tar -zxvf ffmpeg-4.1.tar.gz
cd ffmpeg-4.1/
./configure && make && make install
```
#### 4. 查看是否成功

```
ffmpeg -h
```

#### ps：如果出现libiconv相关错误，解决方法

```
wget https://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.15.tar.gz 
./configure && make && make install

updatedb
locate libiconv.so.2

ln -s /usr/local/lib/libiconv.so.2 /usr/lib/libiconv.so.2
ldconfig
```