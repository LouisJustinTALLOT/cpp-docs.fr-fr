---
title: pgomgr | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70a0615debabb056110dd9d6f7a6aac86e9d464a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198313"
---
# <a name="pgomgr"></a>pgomgr

Ajoute des données de profil à partir d’un ou plusieurs fichiers .pgc au fichier .pgd.

## <a name="syntax"></a>Syntaxe

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Paramètres

*options*<br/>
Les options suivantes peuvent être spécifiées à **pgomgr**:

- **/Help** ou **/ ?** Affichages disponibles **pgomgr** options.

- **/ Effacer** , le fichier .pgd à effacer toutes les informations de profil. Vous ne pouvez pas spécifier un .pgc fichier lorsque **/effacer** est spécifié.

- **/ detail** affiche des statistiques détaillées, y compris les informations de couverture du graphe de flux.

- **/ summary** affiche les statistiques par fonction.

- **/unique** lorsqu’il est utilisé avec **/summary**, entraîne affichage des noms de fonction l'décorés. La valeur par défaut, lorsque **/ unique** n’est pas utilisé, est des noms de fonctions non décorée à afficher.

- **/ fusion**\[**:**<em>n</em>], les données dans le fichier .pgc ou les fichiers à ajouter au fichier .pgd. Le paramètre facultatif, *n*, vous permet de spécifier que les données doivent être ajoutées *n* fois. Par exemple, si un scénario est habituellement effectués six fois afin de refléter la fréquence à laquelle elle est effectuée par les clients, vous pouvez exécuter une fois dans une série de tests et ajoutez-la au fichier .pgd six fois avec **pgomgr/merge:6**.

*pgcfiles*<br/>
Un ou plusieurs fichiers .pgc dont vous souhaitez fusionner dans le fichier .pgd les données de profil. Vous pouvez spécifier un fichier .pgc unique ou plusieurs fichiers .pgc. Si vous ne spécifiez pas de tous les fichiers .pgc, **pgomgr** fusionne tous les fichiers .pgc dont les noms de fichiers sont les mêmes que le fichier .pgd.

*pgdFile* le fichier .pgd dans lequel vous fusionnez des données à partir du fichier .pgc ou les fichiers.

## <a name="remarks"></a>Notes

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

## <a name="example"></a>Exemple

Cet exemple de commande efface le fichier myapp.pgd des données de profil :

`pgomgr /clear myapp.pgd`

Cet exemple de commande ajoute les données de profil dans myapp1.pgc au fichier .pgd trois fois :

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

Dans cet exemple, les données de profil à partir de tous les fichiers myapp # .pgc sont ajoutées au fichier myapp.pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
