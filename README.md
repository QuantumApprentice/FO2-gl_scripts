# FO2-gl_scripts
Global Scripts Preserved for the Post-Apocalypse

Collection of Fallout 2's sFall global scripts which don't have another home.

## [gl_visual_vars](docs/gl_visual_vars-docs/#gl_visual_vars)  
Written by Vennor  
[Download Source](gl_visual_vars/)  
<img src="docs/gl_visual_vars-docs/ScreenShot%20-%20gl_visual_vars%20buttons.png" alt="Buttons menu" width="50%"/>
> This script places 4 buttons at the top of Fallout 2's game window.  
> Used to modify player inventory and stats, and check GVARs and MVARs.  
Known bugs:  
> Traits can't be changed  
> Skills can't be decreased

### Install
Copy pcx\ folder into FO2\data\ folder so it looks like FO2\data\pcx\<br>
Compile gl_visual_vars.ssl and copy resulting gl_visual_vars.int file into FO2\data\scripts<br>

If you have sfall v4.1.9 or greater<br>
you don't have to add lines to ddraw.ini.<br>
If you have sfall v3.7b but less than v4.1.9<br>
Add this line to ddraw.ini:
> ExtraGameMsgFileList=gvar,mvar<br>

This represents gvar.msg and mvar.msg, both of which will need to be created in
> FO2/data/text/english/game/<br>

(possibly substitute your language if sfall supports it)
<br>
<br>
and create gvar.msg with this format:<br>

```
{0}{}{GVAR_PLAYER_REPUTATION}
{1}{}{GVAR_CHILDKILLER_REPUTATION}
{2}{}{GVAR_CHAMPION_REPUTATION}
{3}{}{GVAR_BERSERKER_REPUTATION}
{4}{}{GVAR_BAD_MONSTER}
{5}{}{GVAR_GOOD_MONSTER}
{6}{}{GVAR_PLAYER_MARRIED}
```

and mvar.msg with this format:<br>
```
# [4] [Arroyo Village] [arvillag.h]
{4000}{}{MVAR_Rope_Status}
{4001}{}{MVAR_Tree_Hex}
{4002}{}{MVAR_Gecko_Attack}
{4003}{}{MVAR_Discovery}
```

This is because this script uses sfall's message_str_game() function<br>
link here: https://sfall.bgforge.net/other/#message_str_game<br>
and  here: https://sfall-team.github.io/sfall/other/#message_str_game<br>
but in case the link doesn't work, here's the text:

>message_str_game

>string message_str_game(int fileId, int messageId)

> Works exactly the same as message_str, except you get messages from files in text/english/game folder. Use GAME_MSG_* defines or mstr_* macros from sfall.h to use specific msg file

>    Additional game msg files added by ExtraGameMsgFileList setting will have consecutive fileIds assigned beginning from 0x2000 to 0x2FFF. (e.g. if you set ExtraGameMsgFileList=foo,bar in ddraw.ini, foo.msg will be associated with 0x2000 and bar.msg with 0x2001.).
>    If a file has a specific number assigned in ExtraGameMsgFileList, its fileId will be (0x2000 + assigned number). (e.g. with ExtraGameMsgFileList=foo,bar:2,foobar in ddraw.ini, bar.msg will be associated with 0x2002 and foobar.msg with 0x2003.)

If you're using sfall v4.1.9 or higher, add_extra_msg_file() doesn't require entries in ddraw.ini, and will directly add links to the related .msg files without any extra steps.<br>
link here: https://sfall.bgforge.net/sfall-funcx-macros/#add_extra_msg_file<br>
and  here: https://sfall-team.github.io/sfall/sfall-funcx-macros/#add_extra_msg_file<br>
and the text:

>add_extra_msg_file (sfall.h)

>int add_extra_msg_file(string fileName)

> Loads a custom message file and returns the file ID number assigned to it, in the range of 0x3000 to 0x3FFF, for use with the message_str_game function.

>    fileName: the name of the custom message file (including the .msg extension) in text\<language>\game\ directory.
>    NOTE: if the msg file does not exist in the current language directory, the function will try to load it from the text\English\game\ directory.

> Alternative form: int add_extra_msg_file(string fileName, int fileNumber) [DEPRECATED]

>    Deprecation notice: Starting from sfall 4.4.10/3.8.50, the two-argument form is deprecated. The fileNumber argument is ignored, and the function behaves the same as the one-argument form.


