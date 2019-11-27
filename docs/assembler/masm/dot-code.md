---
title: .CODE
ms.date: 08/30/2018
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: a5b6608ca71a2b406c54a06cd44ac2865211a8ac
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398577"
---
# <a name="code"></a>.CODE

En cas d’utilisation avec [. MODÈLE](../../assembler/masm/dot-model.md), indique le début d’un segment de code.

## <a name="syntax"></a>Syntaxe

> **. CODE** ⟦*nom*⟧

### <a name="parameters"></a>Paramètres

*nom*\
Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est **_TEXT** pour les [modèles](../../assembler/masm/dot-model.md)minuscules, petits, compacts et plats. Le nom par défaut est *modulename*_TEXT pour d’autres modèles.

## <a name="see-also"></a>Voir aussi

Informations de référence sur les [Directives](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
