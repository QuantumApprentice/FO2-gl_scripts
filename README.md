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

This script requires a define in ddraw.ini for files representing
gvar.msg and mvar.msg, both of which will need to be created in
> FO2/data/text/english/game/
(possibly substitute your language if sfall supports it)

Add this line to ddraw.ini (not sure what version):
> ExtraGameMsgFileList=gvar,mvar

and create gvar.msg with this format:<br>
```
{0}{}{GVAR_PLAYER_REPUTATION}       <br>
{1}{}{GVAR_CHILDKILLER_REPUTATION}  <br>
{2}{}{GVAR_CHAMPION_REPUTATION}     <br>
{3}{}{GVAR_BERSERKER_REPUTATION}    <br>
{4}{}{GVAR_BAD_MONSTER}             <br>
{5}{}{GVAR_GOOD_MONSTER}            <br>
{6}{}{GVAR_PLAYER_MARRIED}          <br>
```

and mvar.msg with this format:<br>
```
# [4] [Arroyo Village] [arvillag.h]
{4000}{}{MVAR_Rope_Status}          <br>
{4001}{}{MVAR_Tree_Hex}             <br>
{4002}{}{MVAR_Gecko_Attack}         <br>
{4003}{}{MVAR_Discovery}            <br>
```

This is because this script uses sfall's message_str_game() function
link here: https://sfall.bgforge.net/other/#message_str_game
but in case that doesn't work, here's the text:

```
>message_str_game

>string message_str_game(int fileId, int messageId)

> Works exactly the same as message_str, except you get messages from files in text/english/game folder. Use GAME_MSG_* defines or mstr_* macros from sfall.h to use specific msg file

>    Additional game msg files added by ExtraGameMsgFileList setting will have consecutive fileIds assigned beginning from 0x2000 to 0x2FFF. (e.g. if you set ExtraGameMsgFileList=foo,bar in ddraw.ini, foo.msg will be associated with 0x2000 and bar.msg with 0x2001.).
>    If a file has a specific number assigned in ExtraGameMsgFileList, its fileId will be (0x2000 + assigned number). (e.g. with ExtraGameMsgFileList=foo,bar:2,foobar in ddraw.ini, bar.msg will be associated with 0x2002 and foobar.msg with 0x2003.)
```


