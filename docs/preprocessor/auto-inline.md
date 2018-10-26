---
title: auto_inline | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
dev_langs:
- C++
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc2fb4cb870ff1dca2f0b55e9aad20741ffb8220
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083176"
---
# <a name="autoinline"></a>auto_inline
Exclut toutes les fonctions définies dans la plage où **hors** est spécifié ne soit pas considérée comme des candidats pour l’expansion inline automatique.

## <a name="syntax"></a>Syntaxe

```
#pragma auto_inline( [{on | off}] )
```

## <a name="remarks"></a>Notes

Pour utiliser le **auto_inline** pragma, placez-le avant et immédiatement après (et non dans) une définition de fonction. Le pragma est appliqué à la première définition de fonction après détection du pragma.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)