---
description: 'En savoir plus sur : pragma alloc_text'
title: alloc_text (pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 496a083c251684ebba004eef00bf466e72211ada
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301059"
---
# <a name="alloc_text-pragma"></a>alloc_text (pragma)

Nomme la section de code où les définitions de fonctions spécifiées doivent résider. Le pragma doit intervenir entre un déclarateur de fonction et la définition de fonction pour les fonctions nommées.

## <a name="syntax"></a>Syntaxe

> **#pragma alloc_text (** "*textsection*" **,** *fonction1* [**,** *fonction2* ...] **)**

## <a name="remarks"></a>Notes

Le pragma **alloc_text** ne gère pas les fonctions membres C++ ni les fonctions surchargées. Elle s’applique uniquement aux fonctions déclarées avec la liaison C, c’est-à-dire aux fonctions déclarées avec la spécification de liaison **extern "C"** . Si vous tentez d'utiliser ce pragma sur une fonction avec une liaison C++, une erreur de compilateur est générée.

Étant donné que l’adressage de fonction à l’aide **`__based`** de n’est pas pris en charge, la spécification d’emplacements de section nécessite l’utilisation du pragma **alloc_text** . Le nom spécifié par *textsection* doit être placé entre guillemets doubles.

Le pragma **alloc_text** doit apparaître après les déclarations de l’une des fonctions spécifiées et avant les définitions de ces fonctions.

Les fonctions référencées dans un pragma **alloc_text** doivent être définies dans le même module que le pragma. Sinon, si une fonction non définie est compilée ultérieurement dans une section de texte différente, l’erreur peut être interceptée ou non. En règle générale, le programme fonctionnera correctement, mais la fonction ne sera pas allouée dans les sections prévues.

Les autres limitations sur les **alloc_text** sont les suivantes :

- Elle ne peut pas être utilisée dans une fonction.

- Il doit être utilisé après que la fonction a été déclarée, mais avant que la fonction soit définie.

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
