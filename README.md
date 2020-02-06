# python-4
电话簿主代码
import card_tools
while True:
    card_tools.show_menu()
    action_str = input("请输入序号：")
    print("你选择的序号是[%s]" % action_str)
    if action_str in ["1","2","3"]:
        if action_str == "1":
            card_tools.new_card()
        elif action_str == "2":
            card_tools.show_all()
        elif action_str == "3":
            card_tools.search_card()
    elif action_str == "0":
        print("欢迎下次使用【名片管理系统】")
        break
    else:
        print("输入错误,请输入正确的序号:")
        
   电话簿函数
   #记录所有名片的列表
card_list = []

def show_menu():
    print("*"*50)
    print("欢迎使用名片管理系统")
    print("")
    print("1.新增名片")
    print("2.显示全部")
    print("3.搜索名片")
    print("")
    print("0.退出系统")
    print("*"*50)

def new_card():
    """新增名片"""
    print("-"*50)
    name_str = input("请输入姓名：")
    phone_str = input("请输入电话：")
    qq_str = input("请输入qq：")
    email_str = input("请输入邮箱：")

    card_dict={"name": name_str,
               "phone": phone_str,
               "qq": qq_str,
               "email": email_str}
    card_list.append(card_dict)
    print("已成功添加 %s 的信息" % name_str)


def show_all():
    """显示所有名片"""
    print("-" * 50)
    if len(card_list) == 0:
        print("没有名片记录，请返回添加")
        return
    for name in ["姓名","电话","QQ","邮箱"]:
        print(name,end="\t\t\t")
    print("")
    print("="*50)
    for card_dict in card_list:
        print("%s\t\t\t%s\t\t\t%s\t\t\t%s\t\t\t" % (card_dict["name"],
                                            card_dict["phone"],
                                            card_dict["qq"],
                                            card_dict["email"]))


def search_card():
    """搜索名片"""
    print("-"*50)
    find_name = input("请输入搜索的名字:")
    for card_dict in card_list:
        if card_dict["name"] == find_name:
            print("姓名\t\t电话\t\tQQ\t\t邮箱")
            print("="*50)
            print("%s\t\t\t%s\t\t\t%s\t\t\t%s\t\t\t" % (card_dict["name"],
                                                        card_dict["phone"],
                                                        card_dict["qq"],
                                                        card_dict["email"]))
            break
            deal_card(card_dict)
    else:
        print("没有找到%s" % find_name)

def deal_card(find_dict):
    print(find_dict)
    action_str = input("请选择要执行的操作1.修改 2.删除 0.返回上级主菜单")
    if action_str == '1':
        find_dict["name"] = input_card_info(find_dict["name"],"姓名:")
        find_dict["phone"] = input_card_info( find_dict["phone"],"电话:")
        find_dict["qq"] = input_card_info(find_dict["qq"],"QQ:")
        find_dict["email"] = input_card_info(find_dict["email"],"email:")
        print("修改名片成功")
    elif action_str == '2':
        card_list.remove(find_dict)
        print("删除名片成功")
def input_card_info(dict_value,tip_message):
    result_str = input(tip_message)
    if len(tip_message) > 0:
        return result_str
    else:
        return dict_value
        Linux上的shebang符号（#！）
shebang符号通常再unix系统脚本中的第一行开头使用
指明执行这个脚本文件的解释程序
使用shebang 的步骤
	1.使用which查询python3解释器所在路径
		$ which python3
	2.修改要运行的主python文件，在第一行增加一下内容
		#! /usr/bin/python3
	3.修改主python文件的文件权限，增加执行权限
		$ chmod +x card_main.py
	4.在需要执行程序即可
		./card_main.py

