---
title: Options EDITBIN | Documents Microsoft
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
ms.openlocfilehash: 1922e410b0151337ce403e24d20ae90b7e964cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378520"
---
# <a name="editbin-options"></a>Options EDITBIN
Vous pouvez y recourir pour modifier des fichiers objets, les fichiers exécutables et les bibliothèques de liens dynamiques (DLL). Options spécifient les modifications apportées par EDITBIN.  
  
 Une option se compose d’un spécificateur d’option, qui peut être un tiret (-) ou une barre oblique (/), suivie du nom de l’option. Noms d’options ne peuvent pas être abrégés. Certaines options acceptent des arguments spécifiés après le signe deux-points ( :). Aucun des espaces ou des tabulations ne sont autorisées dans une spécification de l’option. Utilisez un ou plusieurs espaces ou des tabulations pour séparer les spécifications des options sur la ligne de commande. Les noms des options et leurs arguments de mot clé ou les arguments de nom de fichier ne respectent pas la casse. Par exemple, - bind et /BIND ont la même signification.  
  
 EDITBIN comprend les options suivantes :  
  
|Option|Objectif|  
|------------|-------------|  
|[/ALLOWBIND](../../build/reference/allowbind.md)|Spécifie si une DLL peut être liée.|  
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Spécifie le comportement de recherche de manifeste de fichier exécutable ou de DLL.|  
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Spécifie si l’application doit s’exécuter dans un AppContainer — par exemple, une application UWP.|  
|[/BIND](../../build/reference/bind.md)|Définit les adresses pour les points d’entrée dans les objets spécifiés pour accélérer le chargement.|  
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Spécifie si le fichier DLL ou une image exécutable peut être redéfinie de façon aléatoire au moment du chargement en utilisant la randomisation du format d’espace d’adresse (ASLR).|  
|[/ ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Rapports d’erreurs internes à Microsoft.|  
|[/HEAP](../../build/reference/heap.md)|Définit la taille du tas de l’image exécutable en octets.|  
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Spécifie si le fichier DLL ou une image exécutable prend en charge la randomisation du format d’espace de forte entropie (64 bits) adresse (ASLR).|  
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Spécifie s’il faut vérifier la signature numérique lors du chargement.|  
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Spécifie si l’objet prend en charge les adresses supérieures à deux gigaoctets.|  
|[/NOLOGO](../../build/reference/nologo-editbin.md)|Supprime la bannière de démarrage EDITBIN.|  
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Spécifie si l’image exécutable est compatible avec la prévention de l’exécution des données Windows.|  
|[/REBASE](../../build/reference/rebase.md)|Définit les adresses de base pour les objets spécifiés.|  
|[/RELEASE](../../build/reference/release.md)|Définit la somme de contrôle dans l’en-tête.|  
|[/SECTION](../../build/reference/section-editbin.md)|Remplace les attributs d’une section.|  
|[/STACK](../../build/reference/stack.md)|Définit la taille de pile de l’image exécutable en octets.|  
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Spécifie l’environnement d’exécution.|  
|[/SWAPRUN](../../build/reference/swaprun.md)|Spécifie que l’image exécutable doit être copié dans le fichier d’échange et exécutez-le à partir de là.|  
|[/TSAWARE](../../build/reference/tsaware.md)|Spécifie que l’application est conçue pour s’exécuter dans un environnement multi-utilisateur.|  
|[/VERSION](../../build/reference/version.md)|Définit le numéro de version dans l’en-tête.|  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)   
 [Informations de référence sur EDITBIN](../../build/reference/editbin-reference.md)