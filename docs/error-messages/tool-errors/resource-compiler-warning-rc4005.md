---
description: 'En savoir plus sur : avertissement du compilateur de ressources RC4005'
title: 'Avertissement RC4005 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 138037e48356448550308abee8dc43cd06b9ac06
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237125"
---
# <a name="resource-compiler-warning-rc4005"></a>Avertissement RC4005 du compilateur de ressources 

'identificateur' : redéfinition de macro

L’identificateur est défini deux fois. Le compilateur a utilisé la deuxième définition de macro.

Cet avertissement peut être provoqué par la définition d’une macro sur la ligne de commande et dans le code à l’aide d’une `#define` directive. Cela peut également être dû à des macros importées à partir de fichiers include.

Pour éliminer l’avertissement, supprimez l’une des définitions ou utilisez une `#undef` directive avant la deuxième définition.
