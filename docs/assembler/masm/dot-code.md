---
title: .CODE
ms.date: 08/30/2018
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 65d336d2829c97fdf21e6f4b0fcb3063cc7776ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204372"
---
# <a name="code"></a>.CODE

Lorsqu’il est utilisé avec [. MODÈLE](../../assembler/masm/dot-model.md), indique le début d’un segment de code.

## <a name="syntax"></a>Syntaxe

> . CODE [[nom]]

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`name`|Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est _TEXT pour petite, petite, compact et plat [modèles](../../assembler/masm/dot-model.md). Le nom par défaut est *modulename*_TEXT pour d’autres modèles.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)<br/>
[.DATA](../../assembler/masm/dot-data.md)<br/>