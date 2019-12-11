---
title: .CODE
ms.date: 12/06/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 36d9c01d2a24b446ddc91fe73f3cb677067b3e4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987922"
---
# <a name="code-32-bit-masm"></a>. CODE (MASM 32 bits)

En cas d’utilisation avec [. MODÈLE](../../assembler/masm/dot-model.md), indique le début d’un segment de code.

## <a name="syntax"></a>Syntaxe

> **. CODE** ⟦*nom*⟧

### <a name="parameters"></a>Parameters

*nom*\
Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est **_TEXT** pour les [modèles](../../assembler/masm/dot-model.md)minuscules, petits, compacts et plats. Le nom par défaut est *modulename*_TEXT pour d’autres modèles.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
