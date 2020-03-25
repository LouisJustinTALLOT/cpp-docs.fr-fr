---
title: Erreur irrécupérable C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 40a2828ce6b21384ec49c371f23e506d816f1284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204787"
---
# <a name="fatal-error-c1010"></a>Erreur irrécupérable C1010

> fin de fichier inattendue lors de la recherche d'un en-tête précompilé. Avez-vous oublié d’ajouter' #include *Name*'à votre source ?

## <a name="remarks"></a>Notes

Un fichier include spécifié par [/Yu](../../build/reference/yu-use-precompiled-header-file.md) n’est pas listé dans le fichier source. Cette option est activée par défaut dans de nombreux types C++ de projets Visual Studio. Le fichier include par défaut spécifié par cette option est *pch. h*ou *stdafx. h* dans Visual Studio 2017 et versions antérieures.

Dans l’environnement Visual Studio, utilisez l’une des méthodes suivantes pour résoudre cette erreur :

- Vérifiez que vous n’avez pas supprimé par inadvertance, renommé ou supprimé le fichier d’en-tête *pch. h* ou le fichier source *pch. cpp* du projet actuel. (Dans les projets plus anciens, ces fichiers peuvent être nommés *stdafx. h* et *stdafx. cpp*.)

- Assurez-vous que le fichier d’en-tête *pch. h* ou *stdafx. h* est inclus avant toute autre directive de préprocesseur ou de code dans vos fichiers sources. (Dans Visual Studio, ce fichier d’en-tête est spécifié par la propriété du projet **fichier d’en-tête précompilé** .)

- Vous pouvez désactiver l’utilisation d’en-tête précompilé. Si vous désactivez les en-têtes précompilés, cela peut avoir un impact sérieux sur les performances de génération.

### <a name="to-turn-off-precompiled-headers"></a>Pour désactiver les en-têtes précompilés

Pour désactiver l’utilisation d’en-têtes précompilés dans un projet, procédez comme suit :

1. Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le nom du projet, puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **pages de propriétés** du projet.

1. Dans la liste déroulante **configuration** , sélectionnez **toutes les configurations**.

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **en-têtes précompilés** **C/C++**  > .

1. Dans la liste propriété, sélectionnez la liste déroulante pour la propriété **en-tête précompilé** , puis choisissez **ne pas utiliser les en-têtes précompilés**. Choisissez **OK** pour enregistrer vos modifications.

1. Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier source *pch. cpp* dans votre projet. (Dans les projets plus anciens, le fichier peut être nommé *stdafx. cpp*.) Choisissez **exclure du projet** pour le supprimer de la Build.

1. Utilisez la commande de menu **générer** > **nettoyer la solution** pour chaque configuration que vous générez pour supprimer tous les fichiers *PROJECT_NAME. pch* dans vos répertoires de build intermédiaires.

## <a name="see-also"></a>Voir aussi

[Fichiers d’en-tête précompilé](../../build/creating-precompiled-header-files.md)\
[/Yc (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md)
