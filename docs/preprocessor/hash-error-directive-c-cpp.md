---
description: 'En savoir plus sur : directive #error (C/C++)'
title: '#error, directive (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: fd6503de9590893ee0ec53cbbfa59429a0cfdcfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261149"
---
# <a name="error-directive-cc"></a>#error, directive (C/C++)

La directive **#error** émet un message d’erreur spécifié par l’utilisateur au moment de la compilation, puis met fin à la compilation.

## <a name="syntax"></a>Syntaxe

>  *chaîne de jeton de* #error

## <a name="remarks"></a>Notes

Le message d’erreur émis par cette directive comprend le paramètre *de chaîne de jeton* . Le paramètre de *chaîne de jeton* n’est pas soumis à l’expansion macro. Cette directive est particulièrement utile pendant le prétraitement, pour informer le développeur d’une incohérence de programme ou la violation d’une contrainte. L’exemple suivant illustre le traitement des erreurs pendant le prétraitement :

```cpp
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
