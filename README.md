import requests

site = input("target.com : ")
payload = input("payload : ")


def xssurls():
    urls = open("urls.txt", "r")
    urls1 = open("urls1.txt", "w")
    for x in urls:
        if "=" in x:
            urls1.write(x)


def xss():
    urls1 = open("urls1.txt", "r")
    for xx in urls1:
        links = xx.replace("=", f'=">{payload}')
        sa = open("urls2.txt", "a")
        sa.write(links)


def xssfinder():
    urls2 = open("urls2.txt", "r+")
    for xss1 in urls2:
        links = xss1.strip("\n")
        a = requests.get(links)
        if payload in a.text:
            print("xss haya ; " + links)
            xsshaya = open("xsshaya.txt", "a")
            xsshaya.write(links+"\n")
        else:
            print("Xss not be found; " + links)



xssurls()
xss()
xssfinder()
