---
title: detect_mismatch
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: fb6f147f1591f010298e84cb28f05b40dafaeb63
ms.sourcegitcommit: 22f7c4a9b4fc2158fb5283810f15275803cafe10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2019
ms.locfileid: "54417627"
---
# <a name="detectmismatch"></a>detect_mismatch
Place un enregistrement dans un objet. L'éditeur de liens vérifie les éventuelles incompatibilités entre ces enregistrements.

## <a name="syntax"></a>Syntaxe

```
#pragma detect_mismatch("name", "value")
```

## <a name="remarks"></a>Notes

Lorsque vous liez le projet, l'éditeur de liens génère une erreur `LNK2038` si le projet contient deux objets qui ont le même `name` mais qui ont chacun une `value` différente. Utilisez ce pragma pour empêcher la liaison des fichiers objets incohérents.

Le nom et la valeur sont des littéraux de chaîne qui obéissent aux règles des littéraux de chaîne en ce qui concerne les caractères d'échappement et la concaténation. Ils respectent la casse et ne peut pas contenir une virgule, signe égal, entre guillemets, ou le **null** caractère.

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

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
