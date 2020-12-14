---
description: 'En savoir plus sur : Comment : ajouter une DLL native au global assembly cache'
title: 'Comment : ajouter une DLL native au Global Assembly Cache'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: 267bc2f08fdd40da03b71222c48786ab7cc150fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335405"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Comment : ajouter une DLL native au Global Assembly Cache

Vous pouvez placer une DLL native (non COM) dans le global assembly cache.

## <a name="example"></a>Exemple

**/ASSEMBLYLINKRESOURCE** vous permet d’incorporer une DLL native dans un assembly.

Pour plus d’informations, consultez l’article [/ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
