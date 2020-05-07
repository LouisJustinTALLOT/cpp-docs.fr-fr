---
title: Développement des arguments avec caractères génériques
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: f1fb964fe98223fb7187b83c7101027ed1f9cbea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233806"
---
# <a name="expanding-wildcard-arguments"></a>Développement des arguments avec caractères génériques

**Spécifique à Microsoft**

Lors de l’exécution d’un programme C, vous pouvez utiliser l’un des deux caractères génériques (le point d’interrogation (?) et l’astérisque (*)) pour spécifier des arguments de nom de fichier et de chemin sur la ligne de commande.

Par défaut, les caractères génériques ne sont pas développés dans les arguments de ligne de commande. Vous pouvez remplacer la routine de chargement `argv` normale de vecteur des arguments par une version qui développe les caractères génériques en effectuant une liaison avec le fichier setargv.obj ou wsetargv.obj. Si votre programme utilise une `main` fonction, liez-le à Setargv. obj. Si votre programme utilise une `wmain` fonction, liez-le à Wsetargv. obj. Ces deux éléments ont un comportement équivalent.

Pour effectuer une liaison avec setargv.obj ou wsetargv.obj, utilisez l’option **/link** . Par exemple :

**cl example.c /link setargv.obj**

Les caractères génériques sont développés de la même façon que les commandes du système d'exploitation. (Consultez le guide de l'utilisateur de votre système d'exploitation si vous n'êtes pas habitué aux caractères génériques.)

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Options de lien](../c-runtime-library/link-options.md)<br/>
[Fonction main et exécution du programme](../c-language/main-function-and-program-execution.md)
