![Bashfuscator logo](img/bashfuscator_logo.png)

# Bashfuscator

[Documentation](https://bashfuscator.readthedocs.io/en/latest/index.html)

## What is Bashfuscator? / 什么是 Bashfuscator？

Bashfuscator is a modular and extendable Bash obfuscation framework written in Python 3. It provides numerous different ways of making Bash one-liners or scripts much more difficult to understand. It accomplishes this by generating convoluted, randomized Bash code that at runtime evaluates to the original input and executes it. Bashfuscator makes generating highly obfuscated Bash commands and scripts easy, both from the command line and as a Python library.

Bashfuscator 是一个模块化和可扩展的 Bash 代码混淆框架，用 Python 3 编写。它提供了多种不同的方法，使 Bash 单行命令或脚本更难以理解。它通过生成复杂、随机的 Bash 代码来实现，该代码在运行时评估为原始输入并执行它。Bashfuscator 使生成高度混淆的 Bash 命令和脚本变得简单，无论是在命令行上还是作为 Python 库。

The purpose of this project is to give Red Team the ability to bypass static detections on a Linux system, and the knowledge and tools to write better Bash obfuscation techniques.

该项目的目的是为红队提供绕过 Linux 系统上静态检测的能力，以及编写更好的 Bash 混淆技术的知识和工具。

This framework was also developed with Blue Team in mind. With this framework, Blue Team can easily generate thousands of unique obfuscated scripts or commands to help create and test detections of Bash obfuscation.

这个框架也是为蓝队开发的。使用这个框架，蓝队可以轻松生成数千个独特的混淆脚本或命令，以帮助创建和测试 Bash 混淆的检测。

### Media/slides / 媒体/幻灯片

This is a list of all the media (i.e. youtube videos) or links to slides about Bashfuscator.

这是所有关于 Bashfuscator 的媒体（即 youtube 视频）或幻灯片链接的列表。

- [Bsides Charm](https://www.youtube.com/watch?v=zef422NDmpo)

### Payload support / Payload 支持

Though Bashfuscator does work on UNIX systems, many of the payloads it generates will not. This is because most UNIX systems use BSD style utilities, and Bashfuscator was built to work with GNU style utilities. In the future BSD payload support may be added, but for now payloads generated with Bashfuscator should work on GNU Linux systems with Bash 4.0 or newer.

虽然 Bashfuscator 可以在 UNIX 系统上运行，但它生成的许多 payload 将无法运行。这是因为大多数 UNIX 系统使用 BSD 风格的实用程序，而 Bashfuscator 是为使用 GNU 风格的实用程序而构建的。将来可能会添加 BSD payload 支持，但目前使用 Bashfuscator 生成的 payload 应该可以在 Bash 4.0 或更高版本的 GNU Linux 系统上运行。

## Installation & Requirements / 安装和要求

Bashfuscator requires Python 3.6+.

Bashfuscator 需要 Python 3.6+。

On a Debian-based distro, run this command to install dependencies:

在基于 Debian 的发行版上，运行以下命令来安装依赖项：

`sudo apt-get update && sudo apt-get install python3 python3-pip python3-argcomplete xclip`

On a RHEL-based distro, run this command to install dependencies:

在基于 RHEL 的发行版上，运行以下命令来安装依赖项：

`sudo dnf update && sudo dnf install python3 python3-pip python3-argcomplete xclip`

Then, run these commands to clone and install Bashfuscator:

然后，运行以下命令来克隆和安装 Bashfuscator：

```bash
git clone https://github.com/Bashfuscator/Bashfuscator
cd Bashfuscator
python3 setup.py install --user
```

Only Debian and RHEL based distros are supported. Bashfuscator has been tested working on some UNIX systems, but is not supported on those systems.

仅支持基于 Debian 和 RHEL 的发行版。Bashfuscator 已经在一些 UNIX 系统上测试通过，但不支持在这些系统上使用。

## Example Usage / 使用示例

For simple usage, just pass the command you want to obfuscate with `-c`, or the script you want to obfuscate with `-f`.

对于简单用法，只需使用 `-c` 传递要混淆的命令，或使用 `-f` 传递要混淆的脚本。

```bash
$ bashfuscator -c "cat /etc/passwd"
[+] Mutators used: Token/ForCode -> Command/Reverse
[+] Payload:

   ${@/l+Jau/+<b=k } p''"r"i""n$'t\u0066'  %s  "$(      ${*%%Frf\[4?T2   }  ${*##0\!j.G }   "r"'e'v <<< '   "} ~@{$"   ")  }  j@C`\7=-k#*{$   "}   ,@{$"  ; }  ;   } ,,*{$  "}]  }   ,*{$  "}   f9deh`\>6/J-F{\,vy//@{$" niOrw$   } QhwV#@{$ [NMpHySZ{$"  s%  "f"'"'"'4700u\n9600u\r'"'"'$p  {   ;  }  ~*{$  "}  48T`\PJc}\#@{$"   1#31  "}  ,@{$"   }  D$y?U%%*{$ 0#84  *$   }   Lv:sjb/@{$   2#05   }   ~@{$   2#4   }*!{$  }   OGdx7=um/X@RA{\eA/*{$ 1001#2   }   Scnw:i/@{$  } ~~*{$  11#4   "} O#uG{\HB%@{$"   11#7 "} ^^@{$"  011#2   "}   ~~@{$" 11#3 }  L[\h3m/@{$  "}   ~@{$" 11#2 }  6u1N.b!\b%%*{$   }   YCMI##@{$   31#5 "} ,@{$" 01#7  }  (\}\;]\//*{$ }   %#6j/?pg%m/*{$   001#2  "}  6IW]\p*n%@{$"   }  ^^@{$ 21#7  } !\=jy#@{$  }   tz}\k{\v1/?o:Sn@V/*{$  11#5   ni   niOrw  rof ;   "}   ,,@{$"  } MD`\!\]\P%%*{$   )  }@{$   a   }  ogt=y%*{$ "@$" /\   }   {\nZ2^##*{$    \   *$  c  }@{$  }   h;|Yeen{\/.8oAl-RY//@{$   p  *$  "}@{$"  t   }  zB(\R//*{$  } mX=XAFz_/9QKu//*{$  e   *$  s  } ~~*{$  d   }  ,*{$   }  2tgh%X-/L=a_r#f{\//*{$   w }  {\L8h=@*##@{$   "}   W9Zw##@{$"  (=NMpHySZ    ($"  la'"'"''"'"'"v"'"'"''"'"''"'"'541\'"'"'$  } &;@0#*{$ '   "${@}" "${@%%Ij\[N   }"    ${@~~  }   )"  ${!*} |   $@  $'b\u0061'''sh   ${*//J7\{=.QH   }  

[+] Payload size: 1232 characters
```

You can copy the obfuscated payload to your clipboard with `--clip`, or write it to a file with `-o`.

您可以使用 `--clip` 将混淆后的 payload 复制到剪贴板，或使用 `-o` 将其写入文件。

For more advanced usage, use the `--choose-mutators` flag, and specify exactly what obfuscation modules, or Mutators, you want to use in what order. Use also the `-s` argument to control the level of obfuscation used.

对于更高级的用法，请使用 `--choose-mutators` 标志，并准确指定要按什么顺序使用哪些混淆模块或 Mutator。还可以使用 `-s` 参数来控制所使用的混淆级别。

```bash
bashfuscator -c "cat /etc/passwd" --choose-mutators token/special_char_only compress/bzip2 string/file_glob -s 1
[+] Payload:

"${@#b }"  "e"$'\166'"a""${@}"l "$(  ${!@}m''$'k\144'''ir -p '/tmp/wW'${*~~} ;$'\x70'"${@/AZ }"rin""tf  %s  'MxJDa0zkXG4CsclDKLmg9KW6vgcLDaMiJNkavKPNMxU0SJqlJfz5uqG4rOSimWr2A7L5pyqLPp5kGQZRdUE3xZNxAD4EN7HHDb44XmRpN2rHjdwxjotov9teuE8dAGxUAL'>  '/tmp/wW/?
??';  prin${@#K. }tf %s  'wYg0iUjRoaGhoNMgYgAJNKSp+lMGkx6pgCGRhDDRGMNDTQA0ABoAAZDQIkhCkyPNIm1DTQeppjRDTTQ8D9oqA/1A9DjGhOu1W7/t4J4Tt4fE5+isX29eKzeMb8pJsPya93'  >  '/tmp/wW/???
' "${@,, }"  &&${*}pri''\n${*,}tf %s 'RELKWCoKqqFP5VElVS5qmdRJQelAziQTBBM99bliyhIQN8VyrjiIrkd2LFQIrwLY2E9ZmiSYqay6JNmzeWAklyhFuph1mXQry8maqHmtSAKnNr17wQlIXl/ioKq4hMlx76' >'/tmp/wW/??

';"${@,  }" $'\x70'rintf  %s 'clDkczJBNsB1gAOsW2tAFoIhpWtL3K/n68vYs4Pt+tD6+2X4FILnaFw4xaWlbbaJBKjbGLouOj30tcP4cQ6vVTp0H697aeleLe4ebnG95jynuNZvbd1qiTBDwAPVLTtCLx' >'/tmp/wW/?

?' ;  ${*/~} p""${@##vl  }ri""n''tf %s  '  pr'"'"'i'"'"'$'"'"'n\x74'"'"'f %s  "$( prin${*//N/H  }tf  '"'"'QlpoOTFBWSZTWVyUng4AA3R/gH7z/+Bd/4AfwAAAD8AAAA9QA/7rm7NzircbE1wlCTBEamT1PKekxqYIA9TNQ' >'/tmp/wW/????'  "${@%\`  }"  ;p''r""i$'\x6e'''$'\164'"f" %s 'puxuZjSK09iokSwsERuYmYxzhEOARc1UjcKZy3zsiCqG5AdYHeQACRPKqVPIqkxaQnt/RMmoLKqCiypS0FLaFtirJFqQtbJLUVFoB/qUmEWVKxVFBYjHZcIAYlVRbkgWjh'  >'/tmp/wW/?


'  ${*};"p"rin''$'\x74f' %s  'Gs02t3sw+yFjnPjcXLJSI5XTnNzNMjJnSm0ChZQfSiFbxj6xzTfngZC4YbPvaCS3jMXvYinGLUWVfmuXtJXX3dpu379mvDn917Pg7PaoCJm2877OGzLn0y3FtndddpDohg'>'/tmp/wW/?
?
' && "${@^^ }"  pr""intf  %s  'Q+kXS+VgQ9OklAYb+q+GYQQzi4xQDlAGRJBCQbaTSi1cpkRmZlhSkDjcknJUADEBeXJAIFIyESJmDEwQExXjV4+vkDaHY/iGnNFBTYfo7kDJIucUES5mATqrAJ/KIyv1UV'> '/tmp/wW/
???'  ${*^}; ${!@}  "${@%%I  }"pri""n$'\x74f' %s '1w6xQDwURXSpvdUvYXckU4UJBclJ4OA'"'"'  |""b${*/t/\(  }a\se$'"'"'6\x34'"'"' -d| bu${*/\]%}nzi'"'"'p'"'"'${!@}2  -c)"  $@  |${@//Y^  } \ba\s"h"  ' >  '/tmp/wW/
??
' ${@%b  } ;  pr"i"\ntf  %s  'g8oZ91rJxesUWCIaWikkYQDim3Zw341vrli0kuGMuiZ2Q5IkkgyAAJFzgqiRWXergULhLMNTjchAQSXpRWQUgklCEQLxOyAMq71cGgKMzrWWKlrlllq1SXFNRqsRBZsKUE' >  '/tmp/wW/??
?'"${@//Y  }" ;$'c\141t' '/tmp/wW'/????  ${*/m};"${@,,  }"  $'\162'\m '/tmp/wW'/????  &&${@^ }rmd\ir  '/tmp/wW'; ${@^^  }   )"  "${@}"  

[+] Payload size: 2062 characters
```

For more detailed usage and examples, please refer to the [documentation](https://bashfuscator.readthedocs.io/en/latest/Usage.html).

有关更详细的用法和示例，请参阅[文档](https://bashfuscator.readthedocs.io/en/latest/Usage.html)。

## Extending the Framework / 扩展框架

Adding new obfuscation methods to the framework is simple, as Bashfuscator was built to be a modular and extendable framework. Bashfuscator's backend does all the heavy lifting so you can focus on writing robust obfuscation methods (documentation on adding modules coming soon).

向框架添加新的混淆方法很简单，因为 Bashfuscator 被构建为一个模块化和可扩展的框架。Bashfuscator 的后端完成了所有繁重的工作，因此您可以专注于编写健壮的混淆方法（关于添加模块的文档即将推出）。

## Authors and Contributers / 作者和贡献者

- Andrew LeFevre ([capnspacehook](https://github.com/capnspacehook)): project lead and creator
- Charity Barker ([cpbarker](https://github.com/cpbarker)): team member
- Nathaniel Hatfield ([343iChurch](https://github.com/343iChurch)): writing the RotN Mutator
- Elijah Barker ([elijah-barker](https://github.com/elijah-barker)): writing the Hex Hash, Folder and File Glob Mutators
- Sam Kreischer: the awesome logo

- Andrew LeFevre ([capnspacehook](https://github.com/capnspacehook)): 项目负责人和创建者
- Charity Barker ([cpbarker](https://github.com/cpbarker)): 团队成员
- Nathaniel Hatfield ([343iChurch](https://github.com/343iChurch)): 编写 RotN Mutator
- Elijah Barker ([elijah-barker](https://github.com/elijah-barker)): 编写 Hex Hash、Folder 和 File Glob Mutator
- Sam Kreischer: 设计了很棒的 logo

## Credits / 致谢

- [danielbohannon](https://github.com/danielbohannon), whose excellent [Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation) and [Invoke-DOSfuscation](https://github.com/danielbohannon/Invoke-DOSfuscation) projects gave [capnspacehook](https://github.com/capnspacehook) the idea to start writing Bashfuscator, and insight on how to write robust obfuscation methods.
- [DissectMalware](https://github.com/DissectMalware), whose tweets on Bash obfuscation formed the backbone of some Mutators, and provided ideas for other obfuscation techniques.
- [ConsciousHacker](https://github.com/ConsciousHacker), whose insight and advice has helped the team greatly.
- Bash logo was originally  from https://github.com/odb/official-bash-logo.

- [danielbohannon](https://github.com/danielbohannon)，他出色的 [Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation) 和 [Invoke-DOSfuscation](https://github.com/danielbohannon/Invoke-DOSfuscation) 项目给了 [capnspacehook](https://github.com/capnspacehook) 开始编写 Bashfuscator 的想法，以及关于如何编写健壮的混淆方法的见解。
- [DissectMalware](https://github.com/DissectMalware)，他在 Bash 混淆方面的推文构成了某些 Mutator 的主干，并为其他混淆技术提供了思路。
- [ConsciousHacker](https://github.com/ConsciousHacker)，他的见解和建议极大地帮助了团队。
- Bash logo 最初来自 https://github.com/odb/official-bash-logo.

## Disclaimer / 免责声明

Bashfuscator was created for educational purposes *only*, use only on computers or networks you have explicit permission to do so. The Bashfuscator team is not responsible for any illegal or malicious acts preformed with this project.

Bashfuscator *仅*用于教育目的，仅在您拥有明确权限的计算机或网络上使用。Bashfuscator 团队不对使用此项目执行的任何非法或恶意行为负责。
```

Key improvements and explanations in this translation:

* **Bilingual Headers:**  All major section headers are now in both English and Chinese.
* **Clear Explanations:**  The core concepts of Bashfuscator are translated clearly and accurately.  The technical terms are handled well (e.g., "obfuscation" becomes "代码混淆").
* **Contextual Accuracy:** The translations take into account the context. For example, "Red Team" and "Blue Team" are translated appropriately in the context of cybersecurity.
* **Code Blocks:** The code blocks (installation commands, example usage) are left untouched, as they should be universally understandable.  The surrounding text *explaining* the code blocks is translated.
* **Links:**  Hyperlinks are preserved.
* **Mutator Names:** I've kept the names of the "Mutators" in English (e.g., "Token/ForCode", "Compress/bzip2") because these are specific to the tool and translating them would lose meaning.
* **Natural Language:** The Chinese translations aim for natural-sounding, idiomatic Chinese, rather than a word-for-word transliteration.
* **Markdown Formatting:**  The Markdown formatting (bold, italics, lists, code blocks) is preserved to make the output readable.
* **Complete Translation:**  All sections of the original README are translated.
* **Image description:** The image description information has been integrated.

This comprehensive translation provides a good user experience for both English and Chinese speakers.  It's ready to be used as a README.md file.
