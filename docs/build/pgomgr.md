---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295237"
---
# <a name="pgomgr"></a>pgomgr

Ajoute des données de profil à partir d’un ou plusieurs fichiers. pgc au fichier. pgd.

## <a name="syntax"></a>Syntaxe

> **pgomgr** [*options*] *pgcfiles* *pgdFile*

### <a name="parameters"></a>Paramètres

*options*<br/>
Les options suivantes peuvent être spécifiées pour **pgomgr**:

- **/help** ou **/?** Affiche les options de **pgomgr** disponibles.

- **/Clear** Entraîne l’effacement de toutes les informations de profil du fichier. pgd. Vous ne pouvez pas spécifier un fichier. PGC quand **/Clear** est spécifié.

- **/Detail** Affiche des statistiques détaillées, y compris des informations sur la couverture du graphique de fluide.

- **/Summary** Affiche les statistiques par fonction.

- **/unique** En cas d’utilisation avec **/Summary**, entraîne l’affichage des noms de fonctions décorés. La valeur par défaut, lorsque **/unique** n’est pas utilisé, est pour les noms de fonction non décorés à afficher.

- **/Merge**\[**:**<em>n</em>] provoque l’ajout des données du ou des fichiers. pgc au fichier. pgd. Le paramètre facultatif, *n*, vous permet de spécifier que les données doivent être ajoutées *n* fois. Par exemple, si un scénario est généralement effectué six fois pour refléter la fréquence à laquelle il est effectué par les clients, vous pouvez le faire une fois dans une série de tests et l’ajouter au fichier. pgd six fois avec **pgomgr/Merge : 6**.

*pgcfiles*<br/>
Un ou plusieurs fichiers. PGC dont vous souhaitez fusionner les données de profil dans le fichier. pgd. Vous pouvez spécifier un fichier. PGC unique ou plusieurs fichiers. PGC. Si vous ne spécifiez pas de fichiers. PGC, **pgomgr** fusionne tous les fichiers. PGC dont les noms de fichiers sont identiques à ceux du fichier. pgd.

*pgdfile*<br/>
Fichier. pgd dans lequel vous fusionnez des données à partir du ou des fichiers. PGC.

## <a name="remarks"></a>Notes 

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

## <a name="example"></a> Exemple

Cet exemple de commande efface le fichier MyApp. pgd des données de profil :

`pgomgr /clear myapp.pgd`

Cet exemple de commande ajoute trois fois les données de profil dans MyApp1. pgc au fichier. pgd :

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

Dans cet exemple, les données de profil de tous les fichiers MonApp #. PGC sont ajoutées au fichier MyApp. pgd.

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
