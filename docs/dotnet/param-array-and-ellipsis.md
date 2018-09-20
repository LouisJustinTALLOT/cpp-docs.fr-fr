---
title: Tableau param et points de suspension | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2caf6415fdbceb506b736e209c6e7e384b567c5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384375"
---
# <a name="param-array-and-ellipsis"></a>Tableau Param et points de suspension

Priorité du tableau param pour résoudre des appels de fonction surchargée a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

Dans les Extensions managées et la nouvelle syntaxe, il n’existe aucune prise en charge explicite du tableau param que c# et Visual Basic prennent en charge. Au lieu de cela, un tableau ordinaire signale avec un attribut, comme suit :

```
void Trace1( String* format, [ParamArray]Object* args[] );
void Trace2( String* format, Object* args[] );
```

Bien que ces deux technologies ressemblent, le `ParamArray` attribut marque ceci pour c# ou d’autres langages CLR comme un tableau prenant un nombre variable d’éléments à chaque appel. Le changement de comportement des programmes entre Extensions managées et la nouvelle syntaxe est dans la résolution d’une fonction surchargée définie dans lequel une instance déclare des points de suspension et une seconde déclare un `ParamArray` attribut, comme dans l’exemple suivant est fourni par Artur Laksberg.

```
int fx(...); // 1
int fx( [ParamArray] Int32[] ); // 2
```

Dans les Extensions managées, les points de suspension a priorité sur l’attribut qui est raisonnable dans la mesure où l’attribut n’est pas un aspect formel du langage. Toutefois, dans la nouvelle syntaxe, le tableau param est maintenant pris en charge directement dans le langage, et il est prioritaire sur les points de suspension, car elle est plus fortement typée. Par conséquent, dans les Extensions managées, l’appel

```
fx( 1, 2 );
```

correspond à `fx(...)` tandis que dans la nouvelle syntaxe, il se résout en la `ParamArray` instance. Dans le cas improbable où le comportement de votre programme dépend de l’appel de l’instance de points de suspension sur celle de la `ParamArray`, vous devez modifier la signature ou l’appel.

## <a name="see-also"></a>Voir aussi

[Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)