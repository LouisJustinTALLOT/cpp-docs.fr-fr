---
title: "Comment : récupérer des informations sur les fichiers (C + c++ / CLI) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++], retrieving information about
- FileInfo class
ms.assetid: 8b67f7ad-a048-4437-ac5c-b41809a6018d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0536366e445995d6c4e77d58eb0a48e08207f263
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-retrieve-file-information-ccli"></a>Comment : récupérer les informations d'un fichier (C++/CLI)
L’exemple de code suivant montre la <xref:System.IO.FileInfo> classe. Une fois le nom d’un fichier, vous pouvez utiliser cette classe pour récupérer des informations sur le fichier, telles que la taille du fichier, répertoire, nom complet et date et l’heure de création et de la dernière modification.  
  
 Ce code récupère les informations de fichier Notepad.exe.  
  
## <a name="example"></a>Exemple  
  
```  
// file_info.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<String^>^ args = Environment::GetCommandLineArgs();  
   if (args->Length < 2)  
   {  
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");  
      return -1;  
   }  
  
   FileInfo^ fi = gcnew FileInfo( args[1] );  
  
   Console::WriteLine("file size: {0}", fi->Length );  
  
   Console::Write("File creation date:  ");  
   Console::Write(fi->CreationTime.Month.ToString());  
   Console::Write(".{0}", fi->CreationTime.Day.ToString());  
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());  
  
   Console::Write("Last access date:  ");  
   Console::Write(fi->LastAccessTime.Month.ToString());  
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());  
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)