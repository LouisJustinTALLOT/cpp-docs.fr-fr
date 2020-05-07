---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341194"
---
# <a name="pgosweep"></a>pgosweep

Utilisé dans l’optimisation guidée par profil pour écrire toutes les données de profil d’un programme en cours d’exécution dans le fichier. PGC.

## <a name="syntax"></a>Syntaxe

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Paramètres

*options*<br/>
Facultatif Les valeurs valides pour les *options* sont les suivantes :

- **/?** ou **/Help** affiche le message d’aide.

- **/noreset** conserve le nombre dans les structures de données d’exécution.

*image*<br/>
Le chemin d’accès complet d’un fichier. exe ou. dll qui a été créé à l’aide de l’option [/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)ou [/LTCG : PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) .

*pgcfile*<br/>
Fichier. PGC dans lequel cette commande écrit le nombre de données.

## <a name="remarks"></a>Notes 

La commande **pgosweep** fonctionne sur les programmes qui ont été générés à l’aide de l’option [/GENPROFILE ou/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) , ou l’option Deprecated [: PGINSTRUMENT](reference/ltcg-link-time-code-generation.md) déconseillée. Il interrompt un programme en cours d’exécution et écrit les données de profil dans un nouveau fichier. PGC. Par défaut, la commande réinitialise les nombres après chaque opération d’écriture. Si vous spécifiez l’option **/noreset** , la commande enregistre les valeurs, mais ne les réinitialise pas dans le programme en cours d’exécution. Cette option vous permet d’obtenir des données en double si vous récupérez les données de profil ultérieurement.

Une autre utilisation de **pgosweep** consiste à récupérer les informations de profil uniquement pour le fonctionnement normal de l’application. Par exemple, vous pouvez exécuter **pgosweep** peu de fois après avoir démarré l’application et ignoré ce fichier. Cela supprime les données de profil associées aux coûts de démarrage. Ensuite, vous pouvez exécuter **pgosweep** avant de mettre fin à l’application. Désormais, les données collectées comportent des informations de profil uniquement à partir du moment où l’utilisateur peut interagir avec le programme.

Quand vous nommez un fichier. PGC (à l’aide du paramètre *pgcfile* ), vous pouvez utiliser le format standard, qui est *appname ! n*. PGC. Si vous utilisez ce format, le compilateur trouve automatiquement ces données dans la phase **/LTCG/USEPROFILE** ou **/LTCG : PGO** . Si vous n’utilisez pas le format standard, vous devez utiliser [pgomgr](pgomgr.md) pour fusionner les fichiers. PGC.

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

Pour plus d’informations sur la capture des données de profil à partir de votre fichier exécutable, consultez [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a> Exemple

Dans cet exemple de commande, **pgosweep** écrit les informations de profil actuelles pour MyApp. exe dans myapp ! 1. PGC.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
