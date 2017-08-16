# Zpack
感谢Zpack开源代码，自己调试了2天兼容cocos2dx，理论上支持别的跨平台引擎
使用方法:
ZpExplorer g_explorer;
	zp::String wstr;
	std::string path = "指定的目录";
#if(CC_TARGET_PLATFORM == CC_PLATFORM_WIN32)
	std::wstring temp(path.length(), L' ');
	std::copy(path.begin(), path.end(), temp.begin());
	wstr = temp;
#else
	wstr = path;
#endif
	FileUtils::getInstance()->createDirectory(path);
	g_explorer.create(wstr, _T(""));
	if (g_explorer.open(_T("res.npk")))
	{
		g_explorer.extract(_T("."), wstr);
		FileUtils::getInstance()->addSearchPath(path);
	}
	g_explorer.close();
