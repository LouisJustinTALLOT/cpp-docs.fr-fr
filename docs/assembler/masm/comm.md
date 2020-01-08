---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 0ea02806cae3295af0846baa6c4e9049d54c271b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75315171"
---
# <a name="comm"></a>COMM

Crée une variable commune avec les attributs spécifiés dans la *définition*.

## <a name="syntax"></a>Syntaxe

> *Définition* comm ⟦ __,__ *définition* ... ⟧

## <a name="remarks"></a>Notes

Les variables communes sont allouées par l’éditeur de liens et ne peuvent pas être initialisées. Cela signifie que vous ne pouvez pas dépendre de l’emplacement ou de la séquence de ces variables.

Chaque *définition* se présente sous la forme suivante :

⟦*Language-type*⟧ ⟦**near** | **Far**⟧ _étiquette_ **:** _type_⟦ **:** _Count_⟧

Les arguments *Language-type*, **near**et **Far** sont valides uniquement dans MASM 32 bits.

Le *type Language-Language* facultatif définit les conventions d’affectation de noms pour le nom qui suit. Elle remplace toute langue spécifiée par le **.** Directive de modèle. Le modèle facultatif **near** ou **Far** remplace le modèle de mémoire actuel. L' *étiquette* est le nom de la variable. Le *type* peut être n’importe quel spécificateur de type ([Byte](byte-masm.md), [Word](word.md), etc.) ou un entier spécifiant le nombre d’octets. Le nombre *facultatif spécifie le nombre d'* éléments dans l’objet de données déclaré. Le *nombre* par défaut est un.

## <a name="example"></a>Exemple

Cet exemple crée un tableau d’éléments de 512 octets :

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
