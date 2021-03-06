---
description: 'En savoir plus sur : instructions composées (blocs)'
title: Instructions composées (blocs)
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: 7defb11a30466949d5a9ca5e86ca1e865fbfe4fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318011"
---
# <a name="compound-statements-blocks"></a>Instructions composées (blocs)

Une instruction composée se compose de zéro ou plusieurs instructions placées entre accolades (**{}**). Une instruction composée peut être utilisée partout où une instruction est attendue. Les instructions composées sont généralement appelées « blocs ».

## <a name="syntax"></a>Syntaxe

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Notes

L’exemple suivant utilise une instruction composée comme partie d' *instruction* de l' **`if`** instruction (pour plus d’informations sur la syntaxe, consultez [l’instruction if](../cpp/if-else-statement-cpp.md) ) :

```cpp
if( Amount > 100 )
{
    cout << "Amount was too large to handle\n";
    Alert();
}
else
{
    Balance -= Amount;
}
```

> [!NOTE]
> Comme une déclaration est une instruction, une déclaration peut être l’une des instructions figurant dans l' *instruction-List*. Par conséquent, les noms déclarés au sein d'une instruction composée, mais pas explicitement déclarés comme statiques, ont une portée locale et (pour les objets) une durée de vie locale. Pour plus d’informations sur le traitement des noms avec une étendue locale, consultez [scope](../cpp/scope-visual-cpp.md) .

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble des instructions C++](../cpp/overview-of-cpp-statements.md)
