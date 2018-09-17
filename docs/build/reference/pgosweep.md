---
title: pgosweep | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed12828d9170aac576a97c63b9988bb4b303ef58
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711915"
---
# <a name="pgosweep"></a>pgosweep

Utilisé dans l’optimisation guidée par profil pour écrire toutes les données de profil à partir d’un programme en cours d’exécution dans le fichier .pgc.

## <a name="syntax"></a>Syntaxe

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>Paramètres

*options*<br/>
(Facultatif) Les valeurs valides pour *options* sont :

- **/?** ou **/Help** affiche le message d’aide.

- **/NoReset** conserve le compte dans les structures de données de runtime.

*image*<br/>
Le chemin d’accès complet d’un fichier .exe ou .dll qui a été créé à l’aide de la [/genprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), [/fastgenprofile](genprofile-fastgenprofile-generate-profiling-instrumented-build.md), ou [/LTCG : PGINSTRUMENT](ltcg-link-time-code-generation.md) option.

*pgcfile*<br/>
Le fichier .pgc où cette commande écrit les données de nombres.

## <a name="remarks"></a>Notes

Le **pgosweep** commande fonctionne sur les programmes qui ont été créés à l’aide de la [/GENPROFILE ou /fastgenprofile.](genprofile-fastgenprofile-generate-profiling-instrumented-build.md) option ou déconseillées [/LTCG : PGINSTRUMENT](ltcg-link-time-code-generation.md) option. Elle interrompt un programme en cours d’exécution et écrit les données de profil dans un nouveau fichier .pgc. Par défaut, la commande réinitialise les comptes après chaque opération d’écriture. Si vous spécifiez le **/noreset** option, la commande enregistre les valeurs, mais pas Réinitialisez-les dans le programme en cours d’exécution. Cette option vous donne les données en double si vous récupérez les données de profil ultérieurement.

Une utilisation alternative pour **pgosweep** consiste à récupérer des informations de profil uniquement pour le fonctionnement normal de l’application. Par exemple, vous pouvez exécuter **pgosweep** peu de temps après le démarrage de l’application et d’ignorer ce fichier. Cette action supprimera les données de profil associées à des coûts de démarrage. Ensuite, vous pouvez exécuter **pgosweep** avant la fin de l’application. Les données collectées ont maintenant des informations de profil uniquement à partir du moment que l’utilisateur peut interagir avec le programme.

Lorsque vous nommez un fichier .pgc (à l’aide de la *pgcfile* paramètre) vous pouvez utiliser le format standard, c'est-à-dire *appname ! n*.pgc. Si vous utilisez ce format, le compilateur détecte automatiquement ces données dans le **/LTCG /USEPROFILE** ou **/LTCG : PGO** phase. Si vous n’utilisez pas le format standard, vous devez utiliser [pgomgr](pgomgr.md) pour fusionner les fichiers .pgc.

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir d’une invite de commandes développeur Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

Pour plus d’informations sur la façon de capturer les données de profil à partir de votre fichier exécutable, consultez [PgoAutoSweep](pgoautosweep.md).

## <a name="example"></a>Exemple

Dans cet exemple de commande, **pgosweep** écrit les informations de profil actuelles pour myapp.exe sur myapp ! 1.pgc.

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
