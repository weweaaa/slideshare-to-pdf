# SlideShare to PDF

- Python Version：3.8.5
  - If you can not found python, You can try run script:
    - `sudo add-apt-repository ppa:deadsnakes/ppa`
    - `sudo apt-get update`
    - `sudo apt-get install python3.6`

- A python script to help you back up your SlideShare presentations to PDF.


## Requirements

They can be installed by running:

````
apt-get update
apt-get install -y imagemagick python-bs4 python-lxml
````

This script has been tested on an **WSL2 Ubuntu 20.04**  and requires the following packages:

- [ImageMagick-6](https://github.com/ImageMagick/ImageMagick6)
  - If you get the following error `convert-im6.q16: attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/408.`
    - You can try to modify the `/etc/ImageMagick-6/policy.xml` file
      - Modify the comment in paragraph `<policy domain="coder" rights="none" pattern="PDF" />`
      - to `<policy domain="coder" rights="read | write" pattern="PDF" />`
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/)
- [LXML](http://lxml.de/)
  - If you get the following erro `lxml not found please install it`
    - You can try to run `pip3 install lxml` and `pip3 install tushare`
    - If can not found pip, You can try run `apt install python3-pip`


## Usage

### Just run it

Simply running the script will prompt you to input the SlideShare URL you'd like to download. By default, this file will be saved in the `downloads` directory created in the root of the script.

````
./grub.py
Input the SlideShare URL you want to convert: [SLIDE URL]
Reading SlideShare page...
Downloading slide 1...
Downloading slide 2...
[...]
Converting to PDF...
Your file has been successfully created at downloads/[SLIDE NAME].pdf
````


### Run it with Arguments

```
./grub.py [-i|--input <url>] [-o|--output <path>] [-j|--jpg] [--use_convert] [-q|--quiet]
```

#### Input
Specify the SlideShare URL you'd like to download with `-i`.

````
./grub.py -i <SLIDESHARE URL>
````


#### Output
You can specify where to save your PDF with `-o`. The script will accept a directory or a file path. If only the directory path is specified, the name of the slide will be used.

````
./grub.py -o <FOLDER OR FILE PATH>

# save in directory
./grub.py -i [...] -o /home/user/documents/

# save to file
./grub.py -i [...] -o /home/user/documents/my-slide.pdf
````


#### Keep JPGs
You can request to keep the JPG files using `-j` or `--jpg`. This will export the PDF file and also a directory with all the JPG files that make up the PDF.

````
/my-slides-by-author.pdf
/my-slides-by-author/01.jpg
/my-slides-by-author/02.jpg
/my-slides-by-author/03.jpg
...
````

#### Force use of `convert`
The script will automatically detect if the command `magick` is available and use it by default. If you require the use of `convert` instead use `--use_convert`


#### Quiet
Don't print status messages to stdout.

````
./grub.py -q
````


#### Help
Show help message and exit.

````
./grub.py -h
````


## Development
~~This repository includes a Vagrantfile. If you'd like to collaborate, this should help jumpstart the development process.~~
Have tried debugging on WSL2 and confirmed that it works normally

## Contributors
- [tdrk1980](https://github.com/tdrk1980)
- [weweaaa](https://github.com/weweaaa)
