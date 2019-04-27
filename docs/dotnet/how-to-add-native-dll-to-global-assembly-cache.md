---
title: 'Procédure : Ajouter une DLL Native au Global Assembly Cache'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], native
- GAC (global assembly cache), loading native DLLs
- native DLLs [C++]
ms.assetid: 25e8d78a-b197-4269-b4e9-237a544ab3c8
ms.openlocfilehash: b4b886dfef3185c1b3084ed02abcef1ad2630c11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222796"
---
# <a name="how-to-add-native-dll-to-global-assembly-cache"></a>Procédure : Ajouter une DLL Native au Global Assembly Cache

Vous pouvez placer une DLL native (pas COM) dans le Global Assembly Cache.

## <a name="example"></a>Exemple

**/ASSEMBLYLINKRESOURCE** vous permet d’incorporer une DLL native dans un assembly.

Pour plus d’informations, consultez l’article [/ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)](../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md).

```
/ASSEMBLYLINKRESOURCE:MyComponent.dll
```

## <a name="see-also"></a>Voir aussi

[Utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
