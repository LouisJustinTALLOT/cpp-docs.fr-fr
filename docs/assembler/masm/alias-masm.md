---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 274ac451005015b2693d8674673af574ec781bdc
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399293"
---
# <a name="alias-masm"></a>ALIAS (MASM)

La directive d' **alias** crée un autre nom pour une fonction.  Cela vous permet de créer plusieurs noms pour une fonction, ou de créer des bibliothèques qui permettent à l’éditeur de liens (LINK. exe) de mapper une ancienne fonction à une nouvelle fonction.

## <a name="syntax"></a>Syntaxe

> **Alias \<** _alias_ **> = \<** _nom réel_ **>**

#### <a name="parameters"></a>Paramètres

*nom réel*\
Nom réel de la fonction ou de la procédure.  Les chevrons sont requis.

*alias*\
Autre nom ou alias.  Les chevrons sont requis.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](../../assembler/masm/directives-reference.md)
