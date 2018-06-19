---
title: 'Comment : ajouter une DLL Native au Global Assembly Cache | Documents Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b7363de172eabc664bcde1e3bf42f8cc499e4251
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129536"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Comment : ajouter une DLL native au Global Assembly Cache
Vous pouvez placer une DLL native (pas COM) dans le Global Assembly Cache.  
  
## <a name="example"></a>Exemple  
 **/ASSEMBLYLINKRESOURCE** vous permet d’incorporer une DLL native dans un assembly.  
  
 Pour plus d’informations, consultez l’article [/ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).  
  
```  
/ASSEMBLYLINKRESOURCE:MyComponent.dll  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)