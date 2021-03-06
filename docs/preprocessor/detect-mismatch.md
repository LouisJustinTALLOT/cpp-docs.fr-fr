---
description: 'En savoir plus sur : pragma detect_mismatch'
title: detect_mismatch, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: e57ffac731409fb14b61d35f780ee19094108655
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300734"
---
# <a name="detect_mismatch-pragma"></a>detect_mismatch, pragma

Place un enregistrement dans un objet. L'éditeur de liens vérifie les éventuelles incompatibilités entre ces enregistrements.

## <a name="syntax"></a>Syntaxe

> **#pragma detect_mismatch (** "*Name*" **,** "*value*" **)**

## <a name="remarks"></a>Notes

Lorsque vous liez le projet, l’éditeur de liens lève une erreur [LNK2038](../error-messages/tool-errors/linker-tools-error-lnk2038.md) si le projet contient deux objets qui portent le même *nom* mais dont chacun a une *valeur* différente. Utilisez ce pragma pour empêcher la liaison des fichiers objets incohérents.

Le *nom* et la *valeur* sont des littéraux de chaîne et obéissent aux règles des littéraux de chaîne en ce qui concerne les caractères d’échappement et la concaténation. Ils respectent la casse et ne peuvent pas contenir de virgule, de signe égal, de guillemets ou de caractère **null** .

## <a name="example"></a>Exemple

Cet exemple crée deux fichiers qui ont des numéros de version différents pour la même étiquette de version.

```cpp
// pragma_directive_detect_mismatch_a.cpp
#pragma detect_mismatch("myLib_version", "9")
int main ()
{
   return 0;
}

// pragma_directive_detect_mismatch_b.cpp
#pragma detect_mismatch("myLib_version", "1")
```

Si vous compilez ces deux fichiers à l'aide de la ligne de commande `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, vous recevez l'erreur `LNK2038`.

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
