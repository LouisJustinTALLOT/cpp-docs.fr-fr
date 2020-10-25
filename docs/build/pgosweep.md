---
title: pgosweep
description: Utilisez la commande pgosweep pour écrire des données de profil dans un fichier PGC en vue d’une utilisation dans une optimisation guidée par profil.
ms.date: 10/23/2020
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.openlocfilehash: be96d0f092ff65867c304ddf5eb41c0754f6e4be
ms.sourcegitcommit: bf54b407169900bb668c85a67b31dbc0f069fe65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497182"
---
# <a name="pgosweep"></a>pgosweep

Utilisé dans l’optimisation guidée par profil pour écrire toutes les données de profil d’un programme en cours d’exécution dans le fichier PGC.

## <a name="syntax"></a>Syntax

> **`pgosweep`** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Paramètres

*Options*\
Facultatif Les valeurs valides pour les *options* sont les suivantes :

- **`/?`** ou **`/help`** affiche le message d’aide.

- **`/reset`** réinitialise le nombre à zéro après le balayage. Il s’agit du comportement par défaut.

- **`/pid:n`** nettoie uniquement le PID spécifié, où *n* est le numéro PID.

- **`/wait`** attend la fin du PID spécifié avant de collecter les nombres.

- **`/onlyzero`** n’enregistre pas un fichier PGC, seulement zéro compte.

- **`/pause`** suspend la collecte du nombre sur le système.

- **`/resume`** reprend la collecte du nombre sur le système.

- **`/noreset`** conserve le nombre dans les structures de données du Runtime.

*image*\
Le chemin d’accès complet d’un fichier EXE ou DLL qui a été créé à l’aide de l' [`/GENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) [`/FASTGENPROFILE`](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) option, ou [`/LTCG:PGINSTRUMENT`](reference/ltcg-link-time-code-generation.md) .

*pgcfile*\
Fichier PGC dans lequel cette commande écrit le nombre de données.

## <a name="remarks"></a>Remarques

La **`pgosweep`** commande fonctionne sur les programmes qui ont été créés à l’aide de l’option [ `/GENPROFILE` `/FASTGENPROFILE` ou](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) , ou de l' [`/LTCG:PGINSTRUMENT`](reference/ltcg-link-time-code-generation.md) option déconseillé. Il interrompt un programme en cours d’exécution et écrit les données de profil dans un nouveau fichier PGC. Par défaut, la commande réinitialise les nombres après chaque opération d’écriture. Si vous spécifiez l' **`/noreset`** option, la commande enregistre les valeurs, mais ne les réinitialise pas dans le programme en cours d’exécution. Cette option vous permet d’obtenir des données en double si vous récupérez les données de profil ultérieurement.

Une autre utilisation de **`pgosweep`** est de récupérer les informations de profil uniquement pour le fonctionnement normal de l’application. Par exemple, vous pouvez exécuter **`pgosweep`** peu de fois après avoir démarré l’application et ignoré ce fichier. Cette commande supprime les données de profil associées aux coûts de démarrage. Ensuite, vous pouvez exécuter **`pgosweep`** avant de mettre fin à l’application. Désormais, les données collectées comportent des informations de profil uniquement à partir du moment où l’utilisateur peut interagir avec le programme.

Quand vous nommez un fichier PGC (à l’aide du paramètre *pgcfile* ), vous pouvez utiliser le format standard, qui est *`appname!n.pgc`* . Le *n* représente une valeur numérique de plus en plus pour chaque fichier. Si vous utilisez ce format, le compilateur trouve automatiquement ces données dans la **`/LTCG /USEPROFILE`** **`/LTCG:PGO`** phase ou. Si vous n’utilisez pas le format standard, vous devez utiliser [`pgomgr`](pgomgr.md) pour fusionner les fichiers PGC.

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d’une invite de commandes système ou de l’Explorateur de fichiers.

Pour plus d’informations sur la capture des données de profil à partir de votre fichier exécutable, consultez [`PgoAutoSweep`](pgoautosweep.md) .

## <a name="example"></a>Exemple

Dans cet exemple de commande, **`pgosweep`** écrit les informations de profil actuelles pour *`myapp.exe`* dans *`myapp!1.pgc`* .

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)\
[PgoAutoSweep](pgoautosweep.md)
