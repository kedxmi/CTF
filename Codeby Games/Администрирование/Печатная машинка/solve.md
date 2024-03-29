Перед нами PCAP файл, открываем его в WireShark. 
При изучении файла замечаем, что он состоит из пакетов USB, а значит есть и следы от этих пакетов. В разделе "Leftover Capture Data" обнаруживаем сканкоды клавиш клавиатуры.
---
1. Анализируем файл и выявляем пакеты USB.
2. Ищем сканкоды клавиш в остаточной информации (Leftover Capture Data). <img width="398" alt="image" src="https://github.com/kedxmi/CTF/assets/149513988/5fa669cc-824e-4c50-a1f6-9c3cba4c6e48">

3. Упорядочиваем пакеты по порядку, сохраняя только сканкоды.
4. Создаем txt файл, содержащий только сканкоды клавиш.
5. По принципу обозначений сканкодов пишем скрипт для их преобразования в клавиши:
```
   usb_codes = {
	0x04:"aA", 0x05:"bB", 0x06:"cC", 0x07:"dD", 0x08:"eE", 0x09:"fF",
	0x0A:"gG", 0x0B:"hH", 0x0C:"iI", 0x0D:"jJ", 0x0E:"kK", 0x0F:"lL",
	0x10:"mM", 0x11:"nN", 0x12:"oO", 0x13:"pP", 0x14:"qQ", 0x15:"rR",
	0x16:"sS", 0x17:"tT", 0x18:"uU", 0x19:"vV", 0x1A:"wW", 0x1B:"xX",
	0x1C:"yY", 0x1D:"zZ", 0x1E:"1!", 0x1F:"2@", 0x20:"3#", 0x21:"4$",
	0x22:"5%", 0x23:"6^", 0x24:"7&", 0x25:"8*", 0x26:"9(", 0x27:"0)",
	0x2C:"  ", 0x2D:"-_", 0x2E:"=+", 0x2F:"[{", 0x30:"]}",  0x32:"#~",
	0x33:";:", 0x34:"'\"",  0x36:",<",  0x37:".>"
}
data = ''
for x in open("xd","r").readlines():
	code = int(x[4:6],16)
	print(x[4:6])
	if code == 0:
		continue
	if code == 0x28:
		print('ENTER!')
		print(data)
		data = ''
		continue
	upper = 0
	if int(x[0:2],16) == 0x02 or int(x[0:2],16) == 0x20:
		upper = 1
	data += usb_codes[code][upper]
print(data)
```
6. Подставляем наш txt файл в написанный код и получаем флаг:
7. > `CODEBY{N3_p0mnu_fl4g}`.
