---
title: 'Comment : surveiller les modifications de système de fichiers (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
ms.assetid: 207a3069-e63d-417e-8b56-00ab44f29c52
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e35f8c79267a031b2728b0a9b8b59e7d63987aa3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130703"
---
# <a name="how-to-monitor-file-system-changes-ccli"></a>Comment : surveiller les modifications de système de fichiers (C++/CLI)
Le code suivant utilise des exemple <xref:System.IO.FileSystemWatcher> pour enregistrer les événements correspondant aux fichiers créés, modifiés, supprimés ou renommés. Au lieu d’appeler régulièrement un répertoire pour les modifications apportées aux fichiers, vous pouvez utiliser la <xref:System.IO.FileSystemWatcher> classe pour déclencher des événements lorsqu’une modification est détectée.  
  
## <a name="example"></a>Exemple  
  
```  
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
  
## <a name="see-also"></a>Voir aussi  
 [Espace de noms System.IO](https://msdn.microsoft.com/en-us/library/system.io.aspx)   
 [Fichier et flux de données E/S](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)