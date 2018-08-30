---
title: Gestion de fichiers et e / S (C++ / c++ / CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1d04f918c9c92c2de8ff6b654a8a0d4ee43c2130
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196023"
---
# <a name="file-handling-and-io-ccli"></a>Gestion de fichiers et E/S (C++/CLI)
Illustre diverses opérations de fichier à l’aide de .NET Framework.  
  
 Les rubriques suivantes illustrent l’utilisation des classes définies dans le <xref:System.IO> espace de noms pour effectuer diverses opérations sur les fichiers.  
  
## <a name="enumerate"></a> Énumérer les fichiers dans un répertoire
L’exemple de code suivant montre comment récupérer une liste des fichiers dans un répertoire. En outre, les sous-répertoires sont énumérés. Le code suivant exemple utilise le <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetFiles%2A> et <xref:System.IO.Directory.GetDirectories%2A> méthodes pour afficher le contenu du répertoire C:\Windows.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// enum_files.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ folder = "C:\\";  
   array<String^>^ dir = Directory::GetDirectories( folder );  
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);  
   for (int i=0; i<dir->Length; i++)  
      Console::WriteLine(dir[i]);  
  
   array<String^>^ file = Directory::GetFiles( folder );  
   Console::WriteLine("--== Files inside '{0}' ==--", folder);  
   for (int i=0; i<file->Length; i++)  
      Console::WriteLine(file[i]);  
  
   return 0;  
}  
```  

## <a name="monitor"></a> Modifications de système de fichiers de moniteur
Le code suivant exemple utilise <xref:System.IO.FileSystemWatcher> pour enregistrer les événements correspondant aux fichiers créés, modifiés, supprimés ou renommés. Au lieu d’appeler régulièrement un répertoire pour les modifications apportées aux fichiers, vous pouvez utiliser la <xref:System.IO.FileSystemWatcher> classe afin de déclencher des événements lorsqu’une modification est détectée.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// monitor_fs.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::IO;  
  
ref class FSEventHandler  
{  
public:  
    void OnChanged (Object^ source, FileSystemEventArgs^ e)  
    {  
        Console::WriteLine("File: {0} {1}",   
               e->FullPath, e->ChangeType);  
    }  
    void OnRenamed(Object^ source, RenamedEventArgs^ e)  
    {  
        Console::WriteLine("File: {0} renamed to {1}",   
                e->OldFullPath, e->FullPath);  
    }  
};  
  
int main()  
{  
   array<String^>^ args = Environment::GetCommandLineArgs();  
  
   if(args->Length < 2)  
   {  
      Console::WriteLine("Usage: Watcher.exe <directory>");  
      return -1;  
   }  
  
   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );  
   fsWatcher->Path = args[1];  
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>   
              (NotifyFilters::FileName |   
               NotifyFilters::Attributes |   
               NotifyFilters::LastAccess |   
               NotifyFilters::LastWrite |   
               NotifyFilters::Security |   
               NotifyFilters::Size );  
  
    FSEventHandler^ handler = gcnew FSEventHandler();   
    fsWatcher->Changed += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Created += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Deleted += gcnew FileSystemEventHandler(   
            handler, &FSEventHandler::OnChanged);  
    fsWatcher->Renamed += gcnew RenamedEventHandler(   
            handler, &FSEventHandler::OnRenamed);  
  
    fsWatcher->EnableRaisingEvents = true;  
  
    Console::WriteLine("Press Enter to quit the sample.");  
    Console::ReadLine( );  
}  
```  

## <a name="read_binary"></a> Lire un fichier binaire
L’exemple de code suivant montre comment lire des données binaires à partir d’un fichier, à l’aide de deux classes à partir de la <xref:System.IO?displayProperty=fullName> espace de noms : <xref:System.IO.FileStream> et <xref:System.IO.BinaryReader>. <xref:System.IO.FileStream> représente le fichier réel. <xref:System.IO.BinaryReader> Fournit une interface pour le flux de données qui autorise l’accès binaire.  
  
 L’exemple de code lit un fichier nommé data.bin et contient des entiers au format binaire. Pour plus d’informations sur ce type de fichier, consultez [Comment : écrire un fichier binaire (C++ / c++ / CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// binary_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "data.bin";  
   try  
   {  
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);  
      BinaryReader^ br = gcnew BinaryReader(fs);  
  
      Console::WriteLine("contents of {0}:", fileName);  
      while (br->BaseStream->Position < br->BaseStream->Length)  
         Console::WriteLine(br->ReadInt32().ToString());  
  
      fs->Close( );  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("File '{0}' not found", fileName);  
      else  
         Console::WriteLine("Exception: ({0})", e);  
      return -1;  
   }  
   return 0;  
}  
```  
## <a name="read_text"></a> Lire un fichier texte
L’exemple de code suivant montre comment ouvrir et lire une fichier texte une ligne à la fois, à l’aide de la <xref:System.IO.StreamReader> classe qui est définie dans le <xref:System.IO?displayProperty=fullName> espace de noms. Une instance de cette classe est utilisée pour ouvrir un fichier texte, puis le <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> méthode est utilisée pour récupérer chaque ligne.  
  
 Cet exemple de code lit un fichier nommé textfile.txt et qui contienne du texte. Pour plus d’informations sur ce type de fichier, consultez [Comment : écrire un fichier texte (C++ / c++ / CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// text_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ fileName = "textfile.txt";  
   try   
   {  
      Console::WriteLine("trying to open file {0}...", fileName);  
      StreamReader^ din = File::OpenText(fileName);  
  
      String^ str;  
      int count = 0;  
      while ((str = din->ReadLine()) != nullptr)   
      {  
         count++;  
         Console::WriteLine("line {0}: {1}", count, str );  
      }  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("file '{0}' not found", fileName);  
      else  
         Console::WriteLine("problem reading file '{0}'", fileName);  
   }  
  
   return 0;  
}  
```  

## <a name="retrieve"></a> Récupérer des informations de fichier 
L’exemple de code suivant montre la <xref:System.IO.FileInfo> classe. Lorsque vous avez le nom d’un fichier, vous pouvez utiliser cette classe pour récupérer des informations sur le fichier comme la taille du fichier, répertoire, nom complet et date et l’heure de la création et de la dernière modification.  
  
 Ce code récupère les informations de fichier Notepad.exe.  
  
### <a name="example"></a>Exemple  
  
```cpp  
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

## <a name="write_binary"></a> Écrire un fichier binaire
L’exemple de code suivant illustre l’écriture des données binaires dans un fichier. Deux classes à partir de la <xref:System.IO> espace de noms sont utilisés : <xref:System.IO.FileStream> et <xref:System.IO.BinaryWriter>. <xref:System.IO.FileStream> représente le fichier réel, tandis que <xref:System.IO.BinaryWriter> fournit une interface pour le flux de données qui autorise l’accès binaire.  
  
 L’exemple de code suivant écrit un fichier contenant des entiers au format binaire. Ce fichier peut être lu par le code dans [Comment : lire un fichier binaire (C++ / c++ / CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md).  
  
### <a name="example"></a>Exemple  
  
```cpp  
// binary_write.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<Int32>^ data = {1, 2, 3, 10000};  
  
   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);  
   BinaryWriter^ w = gcnew BinaryWriter(fs);  
  
   try   
   {  
      Console::WriteLine("writing data to file:");  
      for (int i=0; i<data->Length; i++)  
      {  
         Console::WriteLine(data[i]);  
         w->Write(data[i]);  
      }  
   }  
   catch (Exception^)   
   {  
     Console::WriteLine("data could not be written");  
     fs->Close();  
     return -1;  
   }  
  
   fs->Close();  
   return 0;  
}  
```  

## <a name="write_text"></a> Écrire un fichier texte
L’exemple de code suivant montre comment créer un fichier texte et écrire du texte à l’aide de la <xref:System.IO.StreamWriter> (classe), qui est défini dans le <xref:System.IO> espace de noms. Le <xref:System.IO.StreamWriter> constructeur prend le nom du fichier doit être créé. Si le fichier existe, il est remplacé (à moins que vous passiez True comme deuxième <xref:System.IO.StringWriter> argument du constructeur).  
  
 Le fichier est classé à l’aide de la <xref:System.IO.StreamWriter.Write%2A> et <xref:System.IO.TextWriter.WriteLine%2A> fonctions.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// text_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "textfile.txt";  
  
   StreamWriter^ sw = gcnew StreamWriter(fileName);  
   sw->WriteLine("A text file is born!");  
   sw->Write("You can use WriteLine");  
   sw->WriteLine("...or just Write");  
   sw->WriteLine("and do {0} output too.", "formatted");  
   sw->WriteLine("You can also send non-text objects:");  
   sw->WriteLine(DateTime::Now);  
   sw->Close();  
   Console::WriteLine("a new file ('{0}') has been written", fileName);  
  
   return 0;  
}  
```  

## <a name="see-also"></a>Voir aussi   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

 [Fichier et flux de données E/S](https://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)

 [Espace de noms System.IO](https://msdn.microsoft.com/library/system.io.aspx)