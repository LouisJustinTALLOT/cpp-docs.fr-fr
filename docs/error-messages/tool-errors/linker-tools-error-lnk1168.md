---
title: Erreur des outils Éditeur de liens LNK1168
ms.date: 11/04/2016
f1_keywords:
- LNK1168
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
ms.openlocfilehash: f0eb63c124162dbb515782bbd014c556c12de153
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450890"
---
# <a name="linker-tools-error-lnk1168"></a>Erreur des outils Éditeur de liens LNK1168

impossible d'ouvrir nomfichier en écriture

L'éditeur de liens ne peut pas écrire dans `filename`. Il est possible que le fichier soit utilisé et que son handle de fichier soit verrouillé par un autre processus. Il est possible également que vous ne disposiez pas de l'autorisation d'accès en écriture pour le fichier, ou pour le répertoire ou le partage réseau dans lequel il est situé. Cette erreur est souvent due à une situation temporaire, par exemple, un verrou détenu par un programme antiviru, processus d’indexation de recherche un fichier ou un retard lors de la libération d’un verrou détenu par le système de génération Visual Studio.

Pour résoudre ce problème, vérifiez que le handle de fichier de `filename` n'est pas verrouillé, et que vous disposez d'une autorisation d'accès en écriture pour le fichier. S'il s'agit d'un exécutable, vérifiez qu'il n'est pas déjà en cours d'exécution.

Vous pouvez utiliser les utilitaires Windows SysInternals [gérer](/sysinternals/downloads/handle) ou [Process Explorer](/sysinternals/downloads/process-explorer) pour déterminer le processus qui possède un fichier de handle de verrou sur `filename`. Vous pouvez également utiliser Process Explorer pour libérer les verrous des handles de fichiers ouverts. Pour plus d'informations sur l'utilisation de ces utilitaires, consultez les fichiers d'aide qui les accompagnent.

Si le fichier est verrouillé par un antivirus, vous pouvez résoudre ce problème en excluant les répertoires de sortie de génération de l'analyse automatique de l'antivirus. Les scanners antivirus sont souvent déclenchés par la création de fichiers dans le système de fichiers. Par ailleurs, ils verrouillent les fichiers pendant l‘analyse. Consultez la documentation de votre antivirus pour plus d'informations sur la façon d'exclure des répertoires spécifiques de l'analyse.

Si le fichier est verrouillé par un service d'indexation de la recherche, vous pouvez résoudre ce problème en excluant les répertoires de sortie de génération de l'indexation automatique. Consultez la documentation du service d'indexation pour plus d'informations. Pour modifier la recherche Windows service d’indexation, utilisez **Options d’indexation** dans le Windows **le panneau de configuration**. Pour plus d’informations, consultez [rechercher l’indexation dans Windows 10 : FORUM AUX QUESTIONS](https://support.microsoft.com/help/4098843/windows-10-search-indexing-faq).

Si votre exécutable ne peut pas être remplacé par le processus de génération, cela signifie qu'il est peut-être verrouillé par l'Explorateur de fichiers. Si le **Application expérience** service a été désactivé, l’Explorateur de fichiers peut conserver un verrou de handle de fichier exécutable pendant une période prolongée. Pour résoudre ce problème, exécutez **services.msc** , puis ouvrez le **propriétés** boîte de dialogue pour le **Application expérience** service. Modifier le **type de démarrage** à partir de **désactivé** à **manuel**.
