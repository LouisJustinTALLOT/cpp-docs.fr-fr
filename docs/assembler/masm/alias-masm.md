---
description: 'En savoir plus sur : ALIAS'
title: ALIAS (MASM)
ms.date: 12/17/2019
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: 7d5072cec8ef56f3dd2202617b3274c958a25d66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97121756"
---
# <a name="alias"></a>ALIAS

La directive d' **alias** crée un autre nom pour une fonction.  Cela vous permet de créer plusieurs noms pour une fonction, ou de créer des bibliothèques qui permettent à l’éditeur de liens (LINK.exe) de mapper une ancienne fonction à une nouvelle fonction.

## <a name="syntax"></a>Syntaxe

> **AFFECTÉ \<**_alias_**> = \<**_actual-name_**>**

#### <a name="parameters"></a>Paramètres

*nom réel*\
Nom réel de la fonction ou de la procédure.  Les chevrons sont requis.

*affecté*\
Autre nom ou alias.  Les chevrons sont requis.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)\
[Syntaxe BNF de MASM](masm-bnf-grammar.md)
