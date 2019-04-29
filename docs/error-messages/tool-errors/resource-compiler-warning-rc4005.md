---
title: 'Avertissement RC4005 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 571c4ac285e9477b017dbc21cf9ff733539759d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346182"
---
# <a name="resource-compiler-warning-rc4005"></a>Avertissement RC4005 du compilateur de ressources 

'identificateur' : redéfinition de macro

L’identificateur est défini à deux reprises. Le compilateur a utilisé la deuxième définition de macro.

Cet avertissement peut être provoqué par une macro est définie sur la ligne de commande et dans le code avec un `#define` directive. Elle peut également être due par des macros importées à partir de fichiers include.

Pour éliminer l’avertissement, supprimez une des définitions ou utilisez un `#undef` directive avant la seconde définition.