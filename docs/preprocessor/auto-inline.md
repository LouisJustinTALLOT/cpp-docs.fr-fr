---
description: 'En savoir plus sur : pragma auto_inline'
title: auto_inline, pragma
ms.date: 08/29/2019
f1_keywords:
- auto_inline_CPP
- vc-pragma.auto_inline
helpviewer_keywords:
- pragmas, auto_inline
- auto_inline pragma
ms.assetid: f7624cd1-be76-429a-881c-65c9040acf43
ms.openlocfilehash: f629bbe5dc47ba15bba5b2b55541509f421fcd8c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301046"
---
# <a name="auto_inline-pragma"></a>auto_inline, pragma

Exclut toutes les fonctions définies dans la plage où **off** est spécifié d’être considéré comme des candidats pour l’expansion Inline automatique.

## <a name="syntax"></a>Syntaxe

> **#pragma auto_inline (** [{ **on**  |  **off** }] **)**

## <a name="remarks"></a>Notes

Pour utiliser le pragma **auto_inline** , placez-le avant et immédiatement après, et non à l’intérieur, une définition de fonction. Le pragma prend effet dès que la première définition de fonction est visible après le pragma.

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
