---
description: En savoir plus sur :. CODE
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 3f47b3bf9f345ae39f68b1b21e8f3807f554ea2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132274"
---
# <a name="code"></a>.CODE

(uniquement MASM 32 bits.) En cas d’utilisation avec [. MODÈLE](dot-model.md), indique le début d’un segment de code.

## <a name="syntax"></a>Syntaxe

> **. CODE** ⟦*nom*⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId* **se termine**;; ⟧\

### <a name="parameters"></a>Paramètres

*nomme*\
Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est **_TEXT** pour les [modèles](dot-model.md)minuscules, petits, compacts et plats. Le nom par défaut est *modulename* _TEXT pour d’autres modèles.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[. MÉTADONNÉE](dot-data.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
