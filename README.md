# lua-webclient

非堵塞的lua http库，是对libcurl multi interface（curlm）的简单封装。
可用于大量http、https请求在单线程内非阻塞处理，如游戏服务器和渠道进行用户的账户密码验证。

## 文件说明

	webclient.c 
		webclient 对curlm的封装
		
	webclient.lua
		webclient 在 skynet 中的简单应用
		
	test.lua
		webclient 使用纯lua的示例
		
			
	
## for-skynet

change webclient.c  "int luaopen_webclient_c(lua_State * L)"


$(LUA_CLIB_PATH)/webclient.so : lualib-src/webclient.c | $(LUA_CLIB_PATH)
	$(CC) $(CFLAGS) $(SHARED) -std=c99 -lcurl -Iskynet-src $^ -o $@