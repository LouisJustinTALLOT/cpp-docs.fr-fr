---
description: 'En savoir plus sur : COMM'
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: dc8a9ed97d55b4b6e45cb8057f46885536ba0b2f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120950"
---
# <a name="comm"></a>COMM

Crée une variable commune avec les attributs spécifiés dans la *définition*.

## <a name="syntax"></a>Syntaxe

>  *Définition* comm ⟦__,__ *définition* ... ⟧

## <a name="remarks"></a>Notes

Les variables communes sont allouées par l’éditeur de liens et ne peuvent pas être initialisées. Cela signifie que vous ne pouvez pas dépendre de l’emplacement ou de la séquence de ces variables.

Chaque *définition* se présente sous la forme suivante :

⟦*Language-type*⟧ ⟦**près**  |  **Far**⟧ _étiquette_**:**_type_⟦**:**_Count_⟧

Les arguments *Language-type*, **near** et **Far** sont valides uniquement dans MASM 32 bits.

Le *type Language-Language* facultatif définit les conventions d’affectation de noms pour le nom qui suit. Elle remplace toute langue spécifiée par le **.** Directive de modèle. Le modèle facultatif **near** ou **Far** remplace le modèle de mémoire actuel. L' *étiquette* est le nom de la variable. Le *type* peut être n’importe quel spécificateur de type ([Byte](byte-masm.md), [Word](word.md), etc.) ou un entier spécifiant le nombre d’octets. Le nombre *facultatif spécifie le nombre d'* éléments dans l’objet de données déclaré. Le *nombre* par défaut est un.

## <a name="example"></a>Exemple

Cet exemple crée un tableau d’éléments de 512 octets :

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
