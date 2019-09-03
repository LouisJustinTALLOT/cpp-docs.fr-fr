---
title: auto_inline, pragma
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: 59cda8cb73196215318c9570a5c067786284afaa
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216302"
---
# <a name="auto_inline-pragma"></a>auto_inline, pragma

Exclut toutes les fonctions définies dans la plage où **off** est spécifié d’être considéré comme des candidats pour l’expansion Inline automatique.

## <a name="syntax"></a>Syntaxe

> **#pragma auto_inline (** [{ **on** | **off** }] **)**

## <a name="remarks"></a>Notes

Pour utiliser le pragma **auto_inline** , placez-le avant et immédiatement après, et non à l’intérieur, une définition de fonction. Le pragma prend effet dès que la première définition de fonction est visible après le pragma.

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
