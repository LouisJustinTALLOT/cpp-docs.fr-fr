---
title: Options EDITBIN
ms.date: 11/04/2016
f1_keywords:
- editbin
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
ms.openlocfilehash: e7338c6a45d74aa8efac1b72683cca7661c62e0a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820102"
---
# <a name="editbin-options"></a>Options EDITBIN

Vous pouvez y recourir pour modifier des fichiers objets, les fichiers exécutables et les bibliothèques de liens dynamiques (DLL). Options spécifient les modifications apportées par EDITBIN.

Une option est constituée d’un spécificateur d’option, qui est un tiret (-) ou une barre oblique (/), suivie du nom de l’option. Noms d’options ne peuvent pas être abrégés. Certaines options acceptent des arguments qui sont spécifiés après le signe deux-points ( :)). Aucun espace ni les onglets ne sont autorisés au sein de la spécification d’une option. Utiliser un ou plusieurs espaces ou des tabulations pour séparer les spécifications des options sur la ligne de commande. Les noms des options et leurs arguments de mot clé ou les arguments de nom de fichier ne respectent pas la casse. Par exemple, - bind et /BIND ont la même signification.

EDITBIN a les options suivantes :

|Option|Objectif|
|------------|-------------|
|[/ALLOWBIND](allowbind.md)|Spécifie si une DLL peut être liée.|
|[/ALLOWISOLATION](allowisolation.md)|Spécifie le comportement de recherche de manifeste de fichier exécutable ou de DLL.|
|[/APPCONTAINER](appcontainer.md)|Spécifie si l’application doit s’exécuter au sein d’un AppContainer — par exemple, une application UWP.|
|[/BIND](bind.md)|Définit les adresses pour les points d’entrée dans les objets spécifiés pour le temps de chargement de vitesse.|
|[/DYNAMICBASE](dynamicbase.md)|Spécifie si la DLL ou une image exécutable pouvant être aléatoirement redéfinie au moment du chargement à l’aide de randomisation du format d’espace d’adresse (ASLR).|
|[/ERRORREPORT](errorreport-editbin-exe.md)|Signale les erreurs internes à Microsoft.|
|[/HEAP](heap.md)|Définit la taille du tas de l’image exécutable en octets.|
|[/HIGHENTROPYVA](highentropyva.md)|Spécifie si la DLL ou une image exécutable prend en charge de forte entropie (64 bits) espace randomisation d’adresse (ASLR).|
|[/INTEGRITYCHECK](integritycheck.md)|Spécifie s’il faut vérifier la signature numérique au moment du chargement.|
|[/LARGEADDRESSAWARE](largeaddressaware.md)|Spécifie si l’objet prend en charge les adresses supérieures à deux gigaoctets.|
|[/NOLOGO](nologo-editbin.md)|Supprime la bannière de démarrage EDITBIN.|
|[/NXCOMPAT](nxcompat.md)|Spécifie si l’image exécutable est compatible avec la prévention de l’exécution des données Windows.|
|[/REBASE](rebase.md)|Définit les adresses de base pour les objets spécifiés.|
|[/RELEASE](release.md)|Définit la somme de contrôle dans l’en-tête.|
|[/SECTION](section-editbin.md)|Remplace les attributs d’une section.|
|[/STACK](stack.md)|Définit la taille de pile de l’image exécutable en octets.|
|[/SUBSYSTEM](subsystem.md)|Spécifie l’environnement d’exécution.|
|[/SWAPRUN](swaprun.md)|Spécifie que l’image exécutable doit être copié dans le fichier d’échange et puis exécutez à partir de là.|
|[/TSAWARE](tsaware.md)|Spécifie que l’application est conçue pour s’exécuter dans un environnement multi-utilisateur.|
|[/VERSION](version.md)|Définit le numéro de version dans l’en-tête.|

## <a name="see-also"></a>Voir aussi

[Outils de génération MSVC supplémentaires](c-cpp-build-tools.md)<br/>
[Informations de référence sur EDITBIN](editbin-reference.md)
