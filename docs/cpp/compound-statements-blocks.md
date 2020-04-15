---
title: Instructions composées (blocs)
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: 60d7e88c5ccccac5a1d967a91c8a82dd954d9afc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337340"
---
# <a name="compound-statements-blocks"></a>Instructions composées (blocs)

Une déclaration composée se compose de zéro ou plus de déclarations enfermées dans**des**accolades bouclées ( . Une instruction composée peut être utilisée partout où une instruction est attendue. Les instructions composées sont généralement appelées « blocs ».

## <a name="syntax"></a>Syntaxe

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Notes

L’exemple suivant utilise une déclaration composée comme partie de *l’instruction* **de l’instruction if** (voir [l’énoncé de si](../cpp/if-else-statement-cpp.md) pour plus de détails sur la syntaxe) :

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
> Étant donné qu’une déclaration est une déclaration, une déclaration peut être l’une des déclarations de la *liste des déclarations*. Par conséquent, les noms déclarés au sein d'une instruction composée, mais pas explicitement déclarés comme statiques, ont une portée locale et (pour les objets) une durée de vie locale. Voir [Scope](../cpp/scope-visual-cpp.md) pour plus de détails sur le traitement des noms à portée locale.

## <a name="see-also"></a>Voir aussi

[Aperçu des déclarations de C](../cpp/overview-of-cpp-statements.md)
