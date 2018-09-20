---
title: typeof va à T::typeid | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4433061fceef455685b6588c81c8c2e434253433
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374672"
---
# <a name="typeof-goes-to-ttypeid"></a>typeof va à T::typeid

Le `typeof` opérateur utilisé dans les Extensions managées pour C++ a été supplanté par le `typeid` mot clé dans Visual C++.

Dans les Extensions managées, le `__typeof()` opérateur retourne associé `Type*` objet quand il est passé le nom d’un type managé. Exemple :

```
// Creates and initializes a new Array instance.
Array* myIntArray =
   Array::CreateInstance( __typeof(Int32), 5 );
```

Dans la nouvelle syntaxe, `__typeof` a été remplacé par une forme supplémentaire de `typeid` qui retourne un `Type^` quand un type managé est spécifié.

```
// Creates and initializes a new Array instance.
Array^ myIntArray =
   Array::CreateInstance( Int32::typeid, 5 );
```

## <a name="see-also"></a>Voir aussi

[Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[typeid](../windows/typeid-cpp-component-extensions.md)