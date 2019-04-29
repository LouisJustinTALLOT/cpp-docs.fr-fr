---
title: '#erreur Directive (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
ms.openlocfilehash: dc229a8eae6938cba32787ecbec6a5aa6a17ab47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383983"
---
# <a name="error-directive-cc"></a>#error, directive (C/C++)
Le **#error** directive émet un message d’erreur spécifié par l’utilisateur au moment de la compilation, puis termine la compilation.

## <a name="syntax"></a>Syntaxe

```
#errortoken-string
```

## <a name="remarks"></a>Notes

Le message d’erreur qui émet cette directive inclut le *chaîne de jeton* paramètre. Le *chaîne de jeton* paramètre n’est pas soumis à une expansion macro. Cette directive est particulièrement utile pendant le prétraitement pour notifier le développeur d’une incohérence de programme ou de la violation d’une contrainte. L’exemple suivant illustre l’erreur lors du traitement pendant le prétraitement :

```
#if !defined(__cplusplus)
#error C++ compiler required.
#endif
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)