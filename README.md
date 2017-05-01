# -
用有道翻译 来进行英汉互译

# coding=gbk
import urllib.request as ask
import urllib.parse as mind
import json
def get_result(word):
    weburl='http://fanyi.youdao.com/translate?smartresult=dict&smartresult=rule&smartresult=ugc&sessionFrom=http://www.youdao.com/'
    data = {
        'type':'AUTO','i':word,'doctype':'json','xmlVersion':'1.8','keyfrom':'fanyi.web','ue':'UTF-8','action':'FY_BY_CLICKBUTTON','typoResult':'true'
    }
    data = mind.urlencode(data).encode('utf-8')
    webheader=ask.urlopen(weburl,data)
    webcontent=webheader.read().decode('utf-8')
    aim=json.loads(webcontent)
    return aim['translateResult'][0][0]['tgt']
if __name__=='__main__':
    while True:
        word = input("请输入要翻译的东东（如要退出请输入exit()）:")
	if word =='exit()':
            	print('退出成功(^_^)!')
            	break;
	else:
            	print('翻译的结果是——》：'+get_result(word))
