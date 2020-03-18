---
title: Options EDITBIN
description: Guide de référence des options de ligne de commande de l’utilitaire Microsoft EDITBIN.
ms.date: 02/09/2020
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: 9fd4170e5ee020780963d83936f1a9fd08d2be11
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439976"
---
# <a name="editbin-options"></a>Options EDITBIN

Vous pouvez utiliser EDITBIN pour modifier des fichiers objets, des fichiers exécutables et des bibliothèques de liens dynamiques (dll). Les options spécifient les modifications apportées par EDITBIN.

Une option se compose d’un spécificateur d’option, qui est un tiret (`-`) ou une barre oblique (`/`), suivi du nom de l’option. Les noms d’options ne peuvent pas être abrégés. Certaines options acceptent les arguments spécifiés après un signe deux-points (`:`). Aucun espace ou onglet n’est autorisé dans une spécification d’option. Utilisez un ou plusieurs espaces ou tabulations pour séparer les spécifications de l’option sur la ligne de commande. Les noms des options et leurs arguments de mot clé ou de nom de fichier ne respectent pas la casse. Par exemple, `-bind` et `/BIND` signifient la même chose.

EDITBIN offre les options suivantes :

|Option|Objectif|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Spécifie si une DLL peut être liée.|
|[/ALLOWISOLATION](allowisolation.md)|Spécifie le comportement de recherche de manifeste de fichier DLL ou exécutable.|
|[/APPCONTAINER](appcontainer.md)|Spécifie si l’application doit s’exécuter dans un AppContainer, par exemple une application UWP.|
|[/BIND](bind.md)|Définit les adresses des points d’entrée dans les objets spécifiés pour accélérer le temps de chargement.|
|[/DYNAMICBASE](dynamicbase.md)|Spécifie si la DLL ou l’image exécutable peut être redéfinie de façon aléatoire au moment du chargement à l’aide de la randomisation du format d’espace d’adresse (ASLR).|
|[/ERRORREPORT](errorreport-editbin-exe.md)| Action déconseillée. Le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|[/HEAP](heap.md)|Définit en octets la taille du tas de l’image exécutable.|
|[/HIGHENTROPYVA](highentropyva.md)|Spécifie si l’image DLL ou exécutable prend en charge la randomisation du format d’espace d’adresse (ASLR) de forte entropie (64 bits).|
|[/INTEGRITYCHECK](integritycheck.md)|Spécifie si la signature numérique doit être vérifiée au moment du chargement.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Spécifie si l’objet prend en charge les adresses de plus de 2 gigaoctets.|
|[/NOLOGO](nologo-editbin.md)|Supprime la bannière de démarrage EDITBIN.|
|[/NXCOMPAT](nxcompat.md)|Spécifie si l’image exécutable est compatible avec la prévention de l’exécution des données Windows.|
|[/REBASE](rebase.md)|Définit les adresses de base pour les objets spécifiés.|
|[/RELEASE](release.md)|Définit la somme de contrôle dans l’en-tête.|
|[/SECTION](section-editbin.md)|Remplace les attributs d’une section.|
|[/STACK](stack.md)|Définit la taille de la pile de l’image exécutable, en octets.|
|[/SUBSYSTEM](subsystem.md)|Spécifie l’environnement d’exécution.|
|[/SWAPRUN](swaprun.md)|Spécifie que l’image exécutable est copiée dans le fichier d’échange, puis exécutée à partir de là.|
|[/TSAWARE](tsaware.md)|Spécifie que l’application est conçue pour s’exécuter dans un environnement multi-utilisateur.|
|[/VERSION](version.md)|Définit le numéro de version dans l’en-tête.|

## <a name="see-also"></a>Voir aussi

[Outils de génération MSVC supplémentaires](c-cpp-build-tools.md)\
[Informations de référence sur EDITBIN](editbin-reference.md)
