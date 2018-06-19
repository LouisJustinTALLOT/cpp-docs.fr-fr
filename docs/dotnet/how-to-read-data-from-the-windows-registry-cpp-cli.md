---
title: 'Comment : lire des données à partir du Registre Windows (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, reading from Windows Registry
- registry, reading
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 87c882bcf2a7900e1f95ea968407c159333c6cb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132552"
---
# <a name="how-to-read-data-from-the-windows-registry-ccli"></a>Comment : lire les données du Registre Windows (C++/CLI)
Le code suivant exemple utilise le <xref:Microsoft.Win32.Registry.CurrentUser> clé pour lire des données à partir du Registre Windows. Tout d’abord, les sous-clés sont énumérées à l’aide de la <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> (méthode), puis la sous-clé Identities est ouverte à l’aide du <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> (méthode). Comme les clés racine, chaque sous-clé est représentée par la <xref:Microsoft.Win32.RegistryKey> classe. Enfin, la nouvelle <xref:Microsoft.Win32.RegistryKey> objet est utilisé pour énumérer les paires clé/valeur.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Notes  
 Le <xref:Microsoft.Win32.Registry> classe est simplement un conteneur pour les instances statiques de <xref:Microsoft.Win32.RegistryKey>. Chaque instance représente un nœud racine de Registre. Les instances sont <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, et <xref:Microsoft.Win32.Registry.Users>.  
  
 En plus d’être statiques, les objets au sein de la <xref:Microsoft.Win32.Registry> classe sont en lecture seule. En outre, les instances de la <xref:Microsoft.Win32.RegistryKey> ne le sont également des objets de classe qui sont créées pour accéder au contenu du Registre. Pour obtenir un exemple illustrant comment substituer ce comportement, consultez [Comment : écrire des données dans le Registre Windows (C + c++ / CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).  
  
 Il existe deux objets supplémentaires dans le <xref:Microsoft.Win32.Registry> classe : <xref:Microsoft.Win32.Registry.DynData> et <xref:Microsoft.Win32.Registry.PerformanceData>. Les deux sont des instances de la <xref:Microsoft.Win32.RegistryKey> classe. Le <xref:Microsoft.Win32.Registry.DynData> objet contient des informations de Registre dynamiques sont uniquement prise en charge dans Windows 98 et Windows Me. Le <xref:Microsoft.Win32.Registry.PerformanceData> objet peut être utilisé pour accéder aux informations de compteur de performances pour les applications qui utilisent le système de surveillance des performances de Windows. Le <xref:Microsoft.Win32.Registry.PerformanceData> nœud représente des informations qui ne sont pas réellement stockées dans le Registre et par conséquent ne peut pas apparaître à l’aide de Regedit.exe.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : écrire des données dans le Registre Windows (C + c++ / CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Opérations Windows (C + c++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)