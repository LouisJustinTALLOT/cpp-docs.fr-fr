---
title: Erreur irrécupérable C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 0315af63e9fdbbb0b136a85a23cb28936dee6836
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273563"
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

1. Sélectionnez la page de propriétés **Propriétés** > de > configuration**C/C++** **en-têtes précompilés** .

1. Dans la liste propriété, sélectionnez la liste déroulante pour la propriété **en-tête précompilé** , puis choisissez **ne pas utiliser les en-têtes précompilés**. Choisissez **OK** pour enregistrer vos modifications.

1. Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier source *pch. cpp* dans votre projet. (Dans les projets plus anciens, le fichier peut être nommé *stdafx. cpp*.) Choisissez **exclure du projet** pour le supprimer de la Build.

1. Utilisez la commande de menu **générer** > une**solution propre** pour chaque configuration que vous générez pour supprimer tous les fichiers *PROJECT_NAME. pch* dans vos répertoires de build intermédiaires.

## <a name="see-also"></a>Voir aussi

[Fichiers d’en-tête précompilés](../../build/creating-precompiled-header-files.md)\
[/YC (créer un fichier d’en-tête précompilé)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (utiliser un fichier d’en-tête précompilé)](../../build/reference/yu-use-precompiled-header-file.md)