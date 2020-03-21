---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 7e53befcc46319d0ecf2287ab96a19a73a0b0b85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076277"
---
# <a name="code"></a>.CODE

(uniquement MASM 32 bits.) En cas d’utilisation avec [. MODÈLE](dot-model.md), indique le début d’un segment de code.

## <a name="syntax"></a>Syntaxe

> **. CODE** ⟦*nom*⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId* **se termine**;; ⟧\

### <a name="parameters"></a>Paramètres

*nom*\
Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est **_TEXT** pour les [modèles](dot-model.md)minuscules, petits, compacts et plats. Le nom par défaut est *modulename*_TEXT pour d’autres modèles.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](directives-reference.md)\
[. ](dot-data.md)\ de données
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
