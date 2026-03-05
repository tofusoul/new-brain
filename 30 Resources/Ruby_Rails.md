- #+BEGIN~SRC~ ruby

#!/usr/bin/env ruby

```
#+END_SRC
```
- RUBY SYSADMIN

``` ruby
File.open("file", "r") do |io| - do something with io end

file = File.new("temp.txt", "w") file.puts("foobar") file.close

puts File.open("temp.txt").atime File.open("temp.txt").chmod(0600)
File.open("temp.txt").chown(1000, 1000)

File.dirname("/home/koan/temp.txt") File.basename("/home/koan/temp.txt")
File.size("/home/koan/temp.txt") File.delete("/home/koan/temp.txt")
File.exists?("/home/koan/temp.txt")
File.directory?("/home/koan/temp.txt")
File.executable?("/home/koan/temp.txt")


Dir['.rb'] #basic globs Dir['**/.rb'] #** == any depth of directory, including current dir. 
#=> array of relative names

File.expand_path('~/file.txt') #=> "/User/mat/file.txt"
File.dirname('dir/file.txt') #=> 'dir' File.basename('dir/file.txt') #=>
'file.txt' File.join('a', 'bunch', 'of', 'strings') #=>
'a/bunch/of/strings' FILE #=> the name of the current file

require 'fileutils' #I know, no underscore is not ruby-like include FileUtils Gives you access (without prepending by 'FileUtils.') to 
- these are basically like unix commands
cd(dir,options)  
pwd() 
mkdir(dir, options)
mkdir(list, options) 
mkdir_p(dir, options) 
mkdir_p(list, options)
rmdir(dir, options) 
rmdir(list, options)
ln(old, new, options) 
ln(list, destdir, options) 
ln_s(old, new, options) 
ln_s(list, destdir, options)
ln_sf(src, dest, options) 
cp(src, dest, options) 
cp(list, dir, options)
cp_r(src, dest, options) 
cp_r(list, dir, options) 
mv(src, dest, options)
mv(list, dir, options) 
rm(list, options)
rm_r(list, options) 
rm_rf(list, options) 
install(src, dest, mode = <src>, options) 
chmod(mode, list, options) 
chmod_R(mode, list, options) 
chown(user, group, list, options)
chown_R(user, group, list, options) 
touch(list, options)
```

- EXAMPLE SCRIPT

``` ruby
#!/usr/bin/env ruby require 'rubygems' gem 'rubyzip'

require 'find' require 'zip/zip'

directory = ARGV[0] 
pattern = “*~” 
Zip::ZipFile.open("backup.zip", Zip::ZipFile::CREATE) do |zipfile| 
  Find.find(directory) do |path|
  filename = File.basename(path) 
  if File.directory?(path) 
    if filename == '.' 
        or filename == '..' 
        Find.prune 
        end 
    else 
        if File.fnmatch(pattern, filename) 
        puts path zipfile.add(path.sub(directory, “”), path) 
        end 
     end
   end 
end
```

- Install Ruby

``` 
sudo apt-get install ruby1.9.1 
sudo apt-get install ruby1.9.1-dev 
sudo ln -s /usr/bin/ruby1.9.1 /usr/bin/ruby 
sudo ln -s /usr/bin/irb1.9.1 /usr/bin/irb 

- Install the dependencies 
sudo apt-get install curl git-core build-essential bison openssl zlib1g zlib1g-dev libssl-dev libsqlite3-0
libsqlite3-dev sqlite3 libxml2-dev libmysqlclient-dev mysql-client
mysql-server autoconf libzlib-ruby libyaml-ruby
```

- Install Rails

- install the latest gem Download from here

<http://rubygems.org/pages/download>

``` 
tar xzvf rubygems-1.8.10.tgz

- Change to the folder and run: 
sudo ruby setup.rb
sudo ln -s /usr/bin/gem1.9.1 /usr/bin/gem - the package manager
#install 'ruby make' 
sudo gem install rake
sudo gem install actionpack

install rails sudo gem install rails

export path "export PATH=/var/lib/gems/1.9.1/bin:$PATH"
```

- check that everything is installed to the latest version \"ruby -v\"

(should be 1.9.2p0) \"gem -v\" (should be 1.8.10) \"rails -v\" (should be 3.1.0)

- Test that things work \"rails new path/to/app\" \"cd /path/to/app\" \"rails

server\" open in browser: \"<http://localhost:3000>\"

- The app should be running!

- Tutorials this is a good place to start:

<http://guides.rubyonrails.org/getting_started.html> and here is the list of doccumentations: <http://rubyonrails.org/documentation>

- Documentation

- <http://www.ruby-lang.org/en/documentation/>
