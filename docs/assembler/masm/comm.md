---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: d36161ba54ca80fc0f576c6f0a7c2a9410bf8075
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541036"
---
# <a name="comm"></a>COMM

Crée une variable commune avec les attributs spécifiés dans la *définition*.

## <a name="syntax"></a>Syntaxe

> *Définition* comm ⟦ __,__ *définition* ... ⟧

## <a name="remarks"></a>Notes

Les variables communes sont allouées par l’éditeur de liens et ne peuvent pas être initialisées. Cela signifie que vous ne pouvez pas dépendre de l’emplacement ou de la séquence de ces variables.

Chaque *définition* se présente sous la forme suivante :

⟦*Language-type*⟧ ⟦**near** | **Far**⟧ _étiquette_ **:** _type_⟦ **:** _Count_⟧

Le *type Language-Language* facultatif définit les conventions d’affectation de noms pour le nom qui suit. Elle remplace toute langue spécifiée par le **.** Directive de modèle. Le modèle facultatif **near** ou **Far** remplace le modèle de mémoire actuel. L' *étiquette* est le nom de la variable. Le *type* peut être n’importe quel spécificateur de type ([Byte](../../assembler/masm/byte-masm.md), [Word](../../assembler/masm/word.md), etc.) ou un entier spécifiant le nombre d’octets. Le nombre *facultatif spécifie le nombre d'* éléments dans l’objet de données déclaré. Le *nombre* par défaut est un.

## <a name="example"></a>Exemple

Cet exemple crée un tableau d’éléments de 512 octets :

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
