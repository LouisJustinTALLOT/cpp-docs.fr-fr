---
title: Développement des caractères génériques
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 1fdea297bb45a06a08bde4f63f90eabef6ddb539
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857175"
---
# <a name="wildcard-expansion"></a>Développement des caractères génériques

**Section spécifique de Microsoft**

Vous pouvez utiliser des caractères génériques (le point d'interrogation (?) et l'astérisque (*)) pour spécifier des arguments de nom de fichier et de chemin d'accès sur la ligne de commande.

Les arguments de ligne de commande sont gérés par une routine appelée `_setargv` (ou `_wsetargv` dans l’environnement à caractères larges), qui, par défaut, ne développe pas les caractères génériques en chaînes séparées dans le tableau de chaînes `argv`. Pour plus d’informations sur l’activation de l’extension de caractères génériques, consultez [extension des arguments génériques](../c-language/expanding-wildcard-arguments.md).

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[main : démarrage du programme](../cpp/main-program-startup.md)