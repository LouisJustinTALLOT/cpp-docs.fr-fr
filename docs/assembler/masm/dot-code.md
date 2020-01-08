---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 0975e96e670400b7fa221ae2d1b9982b5cee613b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314144"
---
# <a name="code"></a>.CODE

(uniquement MASM 32 bits.) En cas d’utilisation avec [. MODÈLE](dot-model.md), indique le début d’un segment de code.

## <a name="syntax"></a>Syntaxe

> **. CODE** ⟦*nom*⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId* **se termine**;; ⟧\

### <a name="parameters"></a>Parameters

*nom*\
Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est **_TEXT** pour les [modèles](dot-model.md)minuscules, petits, compacts et plats. Le nom par défaut est *modulename*_TEXT pour d’autres modèles.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[. ](dot-data.md)\ de données
[Syntaxe BNF de MASM](masm-bnf-grammar.md)

