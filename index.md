# Introduction

In this lab, I must apply my knowledge and  investigate the memory dump of a computer that is potentially affected by malicious activity. I will be doing so with a memory dump of the computer. From what I have gathered, I have found that this is the most effective way to investigate computers as not even a rootkit can be concealed if the investigator is careful enough. For this lab, I will be using the SimSpace virtual machine kali-hunt-20 and the open source memory forensics framework Volatility to investigate the memory dump of a .vmem file named “KobayashiMaru”. The objective here is to gather information about the computer, investigate suspicious files and processes, and, overall, find out what (if anything) is afflicting the computer. 

## Getting Started and Background Information

Using my pre-existing credentials for SimSpace, I log in and access terminal kali-hunt-20. Once logging in, I navigate through the file explorer and find the KobayashiMaru.vmem file in the “shared files” directory. With this located, I then open the application search panel and locate Volatility. To be precise, “Volatility is an open source (sic.) framework used for memory forensics and digital investigation […] It can analyse (sic.) raw memory dumps, crash dumps, virtual machine snapshots, VMware dumps (.vmem) […] and many others” (Open Source For You). This is an especially useful tool as it can investigate the data left on volatile memory which, for reference, refers to the memory that is lost once the computer is powered off. In other words, this is most likely data captured from the computer’s Random-Access Memory (RAM)(ScienceDirect). It is magnanimous, then, that this capture file was made since in a realworld situation, this information would be lost in a matter of hours which would make investigation and diagnosis extremely difficult. Nevertheless, with both materials in my possession, I begin my investigation.

## Initial Observations of the Dump File

Volatility is a Python-based program and is run through the command terminal. As such, to locate my file, I use the command “cd /mnt/share to locate the .vmem file. After some trial and error, I realize that I will need to call the “python” command and specify the “vol.py” file every time I wish to use Volatility. As such, I use the command “python /usr/share/volatility 
vol.py -f KobayashiMaru.vmem imageinfo” to call basic information about the dump file. As mentioned, the first half of the command is me calling the Volatility script and the -f option specifies the memory dump’s file name. The SANS Memory Forensics Cheat Sheet explains that the “imageinfo” plugin “display[s] memory image metadata.” With this command, I can see some preliminary information about the computer from which the memory dump originated.

- <i>Figure 1</i>: The output after using the “imageinfo” command. The first half (up to -f) denotes the Python script call and its directory and the -f option tells Volatility to specifically work on my file. The operating system is found on the line saying, “suggested profiles.” It gives two possibilities, but the true operating system is a 32-bit version of Windows XP Service Package 3 (WinXPSP3x86)

<p align="center">
  <img width="685" height="451" src="assets/fig1.png">
</p>


| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
