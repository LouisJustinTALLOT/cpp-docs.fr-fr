---
title: COMM. | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87bf6d91de052d7ecaf637100b455e66819c748b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690030"
---
# <a name="comm"></a>COMM

Crée une variable naissantes avec les attributs spécifiés dans *définition*.

## <a name="syntax"></a>Syntaxe

> **COMM** *définition* [, *définition*]...

## <a name="remarks"></a>Notes

Variables communes sont allouées par l’éditeur de liens et ne peut pas être initialisés. Cela signifie que vous ne peut pas dépendre de l’emplacement ou la séquence de ces variables.

Chaque *définition* a la forme suivante :

[*langtype*] [**NEAR** &#124; **FAR**] _étiquette_**:**_type_[**:**_nombre_]

Le paramètre facultatif *langtype* définit les conventions d’affectation de noms pour le nom qui suit. Ce paramètre remplace n’importe quel langage spécifié par le **. MODÈLE** directive. Le paramètre facultatif **NEAR** ou **FAR** remplacer le modèle actuel de la mémoire. Le *étiquette* est le nom de la variable. Le *type* peut être n’importe quel spécificateur de type ([octets](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md), et ainsi de suite) ou un entier spécifiant le nombre d’octets. Le paramètre facultatif *nombre* Spécifie le nombre d’éléments dans l’objet de données déclaré ; la valeur par défaut est un.

## <a name="example"></a>Exemple

Cet exemple crée un tableau d’éléments de 512 octets :

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
