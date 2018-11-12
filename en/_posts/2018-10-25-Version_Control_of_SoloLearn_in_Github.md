---
title: Version Control of SoloLearn on Github
last_modified_at: 2018-10-25T00:40:00-06:00
ref: version_control_of_sololearn_on_github
locale: en
categories:
- tutorial
tags:
- github
- sololearn
- bash
- c
- python
- ruby
- php
excerpt: "Version Control of SoloLearn on Github"
header:
  overlay_image: /assets/images/posts/sololearn2github.png
  overlay_filter: 0.5
  show_overlay_excerpt: false
  teaser: /assets/images/posts/sololearn2github_teaser.png
toc: false
toc_sticky: true
classes: wide
---

# Version Control of SoloLearn on Github

## Contents
  * [1. Previous requirements](#1)
  * [2. Create repository on Github](#2)
  * [3. Configure public and private key](#3)
  * [4. Upload files to the repository](#4)
  * [5. Results of changes](#5)

## 1. Previous requirements <a name="1"></a>
   - Accounts in:
     - <i class="fab fa-github"></i> [GitHub](https://github.com)
     - <i class="fas fa-code"></i> [SoloLearn](https://sololearn.com)

## 2. Create repository on Github <a name="2"></a>
   - Click on **New**
     ![](/assets/images/posts/new_repository_1.png)
   - Write the name of the repository **my_codes_in_sololearn** and click on **Create repository**
     ![](/assets/images/posts/new_repository_2.png)
   - Select the connection method to GitHub **https** o **ssh**
     ![](/assets/images/posts/new_repository_3.png)
  
   > **NOTE 1:** In the case of a project of its own, I advise using **ssh** with the use of public and private keys.
  
   > **NOTE 2:** In the case of using **https**, when obtaining changes from the repository no password is required. It is only required when changes are sent to the repository.

## 3. Configure public and private key <a name="3"></a>
   - Create keys using command line (<i class="fab fa-linux"></i> Linux o <i class="fab fa-apple"></i> MAC)

   ```bash
   ssh-keygen -t dsa
   ``` 

   - Create keys using PuTTYgen (<i class="fab fa-windows"></i> Windows)

     ![](/assets/images/posts/puttygen.png)

   > See instructions on [PUTTYGEN - KEY GENERATOR FOR PUTTY ON WINDOWS](https://www.ssh.com/ssh/putty/windows/puttygen)   

  - Assign public key to Github

    - Click on **Settings**

      ![](/assets/images/posts/ssh_keys_01.png)
       
    - Click on **SSH and GPG keys**
      
      ![](/assets/images/posts/ssh_keys_02.png) 

    - Click on **New SSH key**
      ![](/assets/images/posts/ssh_keys_03.png) 
    
    - Copy the **public key** generated to clipboard
      ![](/assets/images/posts/ssh_keys_04.png)
    
    - Paste the **public key** from the clipboard and assign it a **title**, click on **Add SSH key**
      ![](/assets/images/posts/ssh_keys_05.png)

    - Confirm the assignment with the **password** from account
      ![](/assets/images/posts/ssh_keys_06.png)
 
## 4. Upload files to the repository <a name="4"></a>
   - For the first time - [v0.0.1](#v0.0.1)
   
     ```bash
     git init
     git add .
     git commit -m "Mi primera vez!"
     git remote add origin git@github.com:nelbren/my_codes_in_sololearn.git
     git push -u origin master
     ``` 
     ![](/assets/images/posts/git_init.png)
   - For the second time - [v0.0.2](#v0.0.2)
   
     ```bash
     git status
     echo shift_cipher.c.bin > .gitignore
     git add .
     git commit -m "Update to v0.0.2"
     git push
     ``` 
     ![](/assets/images/posts/git_push_v0.0.2.png)
   - For the third time - [v0.0.3](#v0.0.3)
   
     ```bash
     rm shift_cipher.c.bin
     git status
     git add .
     git commit -m "Update to v0.0.3"
     git push
     ``` 
     ![](/assets/images/posts/git_push_v0.0.3.png)     
     
## 5. Results of changes <a name="5"></a> 
   <i class="fab fa-github"></i> [Github](https://github.com/nelbren/my_codes_in_sololearn) (**version control**) versus  <i class="fas fa-code"></i> [SoloLearn](https://www.sololearn.com/Profile/8229204) (**learning/execution environment**)

   |Version|Github         | SoloLearn  |Language| Description|
   |------:|:--------------|:-----------|:------:|:-----------|
   |[0.0.1](https://github.com/nelbren/my_codes_in_sololearn/tree/3bc139e905140e61c67cc7f756efa9df88cdfa90)<a name="v0.0.1"></a>|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/heart.rb)|[heart.rb\_v0.0.1](https://code.sololearn.com/csr5mCY6joG9/#rb)|Ruby|DisplayAHeart-FirstTry!|
   | |[shift\_cipher.c](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.c)|[shift\_cipher\_v0.0.1.c](https://code.sololearn.com/cNGVi1MaeYJ6/#c)|C|UseShiftCipherIn28lines|
   | |[shift\_cipher.c_compile.bash](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.c_compile.bash)| - |Bash|Bash4CompileCProgram|
   | |[shift\_cipher.php](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.php)| [shift\_cipher\_v0.0.1.php](https://code.sololearn.com/w5I5CvnY7TOs/#php)|PHP|UseShiftCipherIn13lines|   
   | |[shift\_cipher.py](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.py)| [shift\_cipher\_v0.0.1.py](https://code.sololearn.com/c2DTb4Eiz4qP/#py)|Python|UseShiftCipherIn10lines|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/shift_cipher.rb)| [shift\_cipher\_v0.0.1.rb](https://code.sololearn.com/cRNWQ2J4He6o/#rb)|Ruby|UseShiftCipherIn20lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/3bc139e905140e61c67cc7f756efa9df88cdfa90/string_rotations.rb)| [string\_rotations\_v0.0.1.rb](https://code.sololearn.com/cZu14adYWt4Q/#rb)|Ruby|UsingSubstring|    
   |[0.0.2](https://github.com/nelbren/my_codes_in_sololearn/tree/d32be705aae9f67bc0535c747cda2ce562c70734)<a name="v0.0.2"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/d32be705aae9f67bc0535c747cda2ce562c70734#diff-b41048bdbaf2311019d6726e7e2c6912)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/heart.rb)|[heart.rb\_v0.0.2](https://code.sololearn.com/cvgkNxueAUCI/#rb)|Ruby|DisplayAHeart-UseShortenedIf!|
   | |[shift\_cipher.c](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/shift_cipher.c)|[shift\_cipher\_v0.0.2.c](https://code.sololearn.com/cOmOJZmV2Fsa/#c)|C|UseTernaryOperatorIn15lines|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/shift_cipher.rb)| [shift\_cipher\_v0.0.2.rb](https://code.sololearn.com/cxVFVuRK9z79/#rb)|Ruby|UseTernaryOperatorIn13lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/d32be705aae9f67bc0535c747cda2ce562c70734/string_rotations.rb)| [string\_rotations\_v0.0.2.rb](https://code.sololearn.com/cKtyRTM49lLc/#rb)|Ruby|UsingRotate|
   |[0.0.3](https://github.com/nelbren/my_codes_in_sololearn/tree/80414f98e31ffb6b18f198c7c491141597cf0117)<a name="v0.0.3"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/80414f98e31ffb6b18f198c7c491141597cf0117?diff=split)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/80414f98e31ffb6b18f198c7c491141597cf0117/heart.rb)|[heart.rb\_v0.0.3](https://code.sololearn.com/c0or8DjaVS2N/#rb)|Ruby|DisplayAHeart-UseShortBlocks1|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/80414f98e31ffb6b18f198c7c491141597cf0117/shift_cipher.rb)| [shift\_cipher\_v0.0.3.rb](https://code.sololearn.com/cpkKE1Vfo4v0/#rb)|Ruby|UseShorthandOperIn11lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/80414f98e31ffb6b18f198c7c491141597cf0117/string_rotations.rb)| [string\_rotations\_v0.0.3.rb](https://code.sololearn.com/cN3W06aB6fDw/#rb)|Ruby|UsingRegex| 
   |[0.0.4](https://github.com/nelbren/my_codes_in_sololearn/tree/b837bb11609c7159e91972b970354c5fbb5f94af)<a name="v0.0.4"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/b837bb11609c7159e91972b970354c5fbb5f94af#diff-b41048bdbaf2311019d6726e7e2c6912)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/b837bb11609c7159e91972b970354c5fbb5f94af/heart.rb)|[heart.rb\_ v0.0.4](https://code.sololearn.com/cjy7I5Qx9B1A/#rb)|Ruby|DisplayAHeart-UseShortBlocks2|
   | |[shift\_cipher.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/b837bb11609c7159e91972b970354c5fbb5f94af/shift_cipher.rb)| [shift\_cipher\_v0.0.4.rb](https://code.sololearn.com/cQN4bIY8A81y/#rb)|Ruby|UseBracketSyntaxIn7lines|  
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/b837bb11609c7159e91972b970354c5fbb5f94af/string_rotations.rb)| [string\_rotations\_v0.0.4.rb](https://code.sololearn.com/c382KXDa3l22/#rb)|Ruby|UsingSubstringAndOnlyOneAssing|
   |[0.0.5](https://github.com/nelbren/my_codes_in_sololearn/tree/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b)<a name="v0.0.4"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b?diff=split)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b/heart.rb)|[heart.rb\_ v0.0.5](https://code.sololearn.com/cTcEJusa6pwj/#rb)|Ruby|DisplayAHeart-UseCase2Array|
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/64ac756c6bbc6f16a9fe4fca47bfdb74a187b86b/string_rotations.rb)| [string\_rotations\_v0.0.5.rb](https://code.sololearn.com/cwGgkvm4839e/#rb)|Ruby|UsingSubstringAndOnlyOneAssingInside|
   |[0.0.6](https://github.com/nelbren/my_codes_in_sololearn/tree/ced9cee8a6aabedf0301a0d290b2ec52f882232e)<a name="v0.0.6"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/ced9cee8a6aabedf0301a0d290b2ec52f882232e)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/ced9cee8a6aabedf0301a0d290b2ec52f882232e/heart.rb)|[heart.rb\_ v0.0.6](https://code.sololearn.com/c86Uo1h25mD2/#rb)|Ruby|DisplayAHeart-UseMultipleAssign|
   | |[string\_rotations.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/ced9cee8a6aabedf0301a0d290b2ec52f882232e/string_rotations.rb)| [string\_rotations\_v0.0.6.rb](https://code.sololearn.com/cWa639epbOuy/#rb)|Ruby|UsingAnCustomFunction|      
   |[0.0.7](https://github.com/nelbren/my_codes_in_sololearn/tree/8b59281b8b81d16404185c31f1a91350d4e11ca2)<a name="v0.0.7"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/8b59281b8b81d16404185c31f1a91350d4e11ca2)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/8b59281b8b81d16404185c31f1a91350d4e11ca2/heart.rb)|[heart.rb\_ v0.0.7](https://code.sololearn.com/cwosAyRtEccI/#rb)|Ruby|DisplayAHeart-GlobalVarsToLocal|
   |[0.0.8](https://github.com/nelbren/my_codes_in_sololearn/tree/9f7d1e2928c2fc02ffb1ee55148bc0c9ca90b90a)<a name="v0.0.8"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/9f7d1e2928c2fc02ffb1ee55148bc0c9ca90b90a)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/9f7d1e2928c2fc02ffb1ee55148bc0c9ca90b90a/heart.rb)|[heart.rb\_ v0.0.8](https://code.sololearn.com/c1ril3v0sx5e/#rb)|Ruby|DisplayAHeart-Array2NewAssign''|
   |[0.0.9](https://github.com/nelbren/my_codes_in_sololearn/tree/5a3e08868a7b381d43fa04ea857841a13675244c)<a name="v0.0.9"></a>\|[diff](https://github.com/nelbren/my_codes_in_sololearn/commit/5a3e08868a7b381d43fa04ea857841a13675244c)|[heart.rb](https://github.com/nelbren/my_codes_in_sololearn/blob/5a3e08868a7b381d43fa04ea857841a13675244c/heart.rb)|[heart.rb\_v0.0.9](https://code.sololearn.com/c6Ke3H0Avdh0/#rb)|Ruby|DisplayAHeart-ReplaceIfForTwoIf|

<center><strong>Made</strong> with <img src="/assets/images/posts/icons8-corazones-24.png" alt="drawing" height="18px" style="display: inline-block; vertical-align: middle;"> <strong>by</strong> Martin <a href="https://nelbren.com" style="color: black; text-decoration: none;"><strong>Nelbren</strong></a> Cuellar</center>
