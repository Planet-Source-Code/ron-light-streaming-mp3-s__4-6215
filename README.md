<div align="center">

## Streaming MP3's


</div>

### Description

This Code when put in any directory will create a HTML page listing all Mp3's in the directory. It also creates a streaming link to the file, so anyone can stream off you MP3's from your server withour downloading them.
 
### More Info
 
None. Just drop it in the directory with your mp3's. This is not a recursive list meaning it only lists those in the current directory.

Html page with streaming links to all mp3's in current dirrectory.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Ron Light](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/ron-light.md)
**Level**          |Intermediate
**User Rating**    |4.9 (34 globes from 7 users)
**Compatibility**  |ASP \(Active Server Pages\), VbScript \(browser/client side\)

**Category**       |[Files](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/files__4-2.md)
**World**          |[ASP / VbScript](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/asp-vbscript.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/ron-light-streaming-mp3-s__4-6215/archive/master.zip)

### API Declarations

If you look at this you owe me royalties! Just kidding.


### Source Code

```
I streamlined my last example:
<HTML>
<HEAD>
<TITLE></TITLE>
</HEAD>
<BODY>
<%
  On Error Resume Next
  Dim FileSystemObject, Folder, FileCollection, File
  Dim FolderPath, WebDir
	If Request.QueryString("play") >"" Then
	  Response.Write "<EMBED src=" & chr(34) & Request.QueryString("play") & chr(34)
	  Response.Write " width=350 height=43 controls=console volume=80"
	  Response.Write " width=350 loop=false type='audio/mp3'>"
	  Response.Write "<BR>"
	End If
  Server.ScriptTimeOut=1
  FolderPath= server.MapPath(".") & "\"
  WebDir= Request.ServerVariables("PATH_INFO")
  Set FileSystemObject = CreateObject("Scripting.FileSystemObject")
  'List All Files
  Set Folder = FileSystemObject.GetFolder(Folderpath)
  Set FileCollection = Folder.Files
  For Each File In FileCollection
		s = LCase(File.Name)
		If ucase(Right(File.name,4))=".MP3" Then
			Response.Write "<A href=" & chr(34) & webdir & "?Play=" & File.name & chr(34) & ">" & File.name & " FileSize=" & File.size & "</A><BR>"
		Else
			'Code To display other file types with a regular link
			'Response.Write "<A href=" & chr(34) & webdir & f1.name & chr(34) & ">" & f1.name & " FileSize=" & f1.size & "</A><BR>"
		End If
  Next
%>
</BODY>
</HTML>
```

