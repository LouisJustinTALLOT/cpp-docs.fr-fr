---
title: 'Comment : écrire des données dans le Registre Windows (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 304bc224be8776c9793af07283c6a5697a4e49eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130800"
---
# <a name="how-to-write-data-to-the-windows-registry-ccli"></a>Comment : écrire des données dans le Registre Windows (C++/CLI)
Le de code suivant montre comment utiliser le <xref:Microsoft.Win32.Registry.CurrentUser> clé à créer une instance accessible en écriture de la <xref:Microsoft.Win32.RegistryKey> classe correspondant à la **logiciel** clé. Le <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> méthode est ensuite utilisée pour créer une nouvelle clé et l’ajouter aux paires clé/valeur.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser le .NET Framework pour accéder au Registre avec le <xref:Microsoft.Win32.Registry> et [RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx) classes, qui sont tous deux définis dans le <xref:Microsoft.Win32> espace de noms. Le **Registre** classe est un conteneur pour les instances statiques de la <xref:Microsoft.Win32.RegistryKey> classe. Chaque instance représente un nœud racine de Registre. Les instances sont <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, et <xref:Microsoft.Win32.Registry.Users>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : lire des données à partir du Registre Windows (C + c++ / CLI)](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)