---
title: Options EDITBIN | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0850f242b8368a9592a5622e627c781b4df4cde5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710136"
---
# <a name="editbin-options"></a>Options EDITBIN

Vous pouvez y recourir pour modifier des fichiers objets, les fichiers exécutables et les bibliothèques de liens dynamiques (DLL). Options spécifient les modifications apportées par EDITBIN.

Une option est constituée d’un spécificateur d’option, qui est un tiret (-) ou une barre oblique (/), suivie du nom de l’option. Noms d’options ne peuvent pas être abrégés. Certaines options acceptent des arguments qui sont spécifiés après le signe deux-points ( :)). Aucun espace ni les onglets ne sont autorisés au sein de la spécification d’une option. Utiliser un ou plusieurs espaces ou des tabulations pour séparer les spécifications des options sur la ligne de commande. Les noms des options et leurs arguments de mot clé ou les arguments de nom de fichier ne respectent pas la casse. Par exemple, - bind et /BIND ont la même signification.

EDITBIN a les options suivantes :

|Option|Objectif|
|------------|-------------|
|[/ALLOWBIND](../../build/reference/allowbind.md)|Spécifie si une DLL peut être liée.|
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Spécifie le comportement de recherche de manifeste de fichier exécutable ou de DLL.|
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Spécifie si l’application doit s’exécuter au sein d’un AppContainer — par exemple, une application UWP.|
|[/BIND](../../build/reference/bind.md)|Définit les adresses pour les points d’entrée dans les objets spécifiés pour le temps de chargement de vitesse.|
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Spécifie si la DLL ou une image exécutable pouvant être aléatoirement redéfinie au moment du chargement à l’aide de randomisation du format d’espace d’adresse (ASLR).|
|[/ ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Signale les erreurs internes à Microsoft.|
|[/HEAP](../../build/reference/heap.md)|Définit la taille du tas de l’image exécutable en octets.|
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Spécifie si la DLL ou une image exécutable prend en charge de forte entropie (64 bits) espace randomisation d’adresse (ASLR).|
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Spécifie s’il faut vérifier la signature numérique au moment du chargement.|
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Spécifie si l’objet prend en charge les adresses supérieures à deux gigaoctets.|
|[/NOLOGO](../../build/reference/nologo-editbin.md)|Supprime la bannière de démarrage EDITBIN.|
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Spécifie si l’image exécutable est compatible avec la prévention de l’exécution des données Windows.|
|[/REBASE](../../build/reference/rebase.md)|Définit les adresses de base pour les objets spécifiés.|
|[/RELEASE](../../build/reference/release.md)|Définit la somme de contrôle dans l’en-tête.|
|[/SECTION](../../build/reference/section-editbin.md)|Remplace les attributs d’une section.|
|[/STACK](../../build/reference/stack.md)|Définit la taille de pile de l’image exécutable en octets.|
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Spécifie l’environnement d’exécution.|
|[/SWAPRUN](../../build/reference/swaprun.md)|Spécifie que l’image exécutable doit être copié dans le fichier d’échange et puis exécutez à partir de là.|
|[/TSAWARE](../../build/reference/tsaware.md)|Spécifie que l’application est conçue pour s’exécuter dans un environnement multi-utilisateur.|
|[/VERSION](../../build/reference/version.md)|Définit le numéro de version dans l’en-tête.|

## <a name="see-also"></a>Voir aussi

[Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[Informations de référence sur EDITBIN](../../build/reference/editbin-reference.md)