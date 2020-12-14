---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1168'
title: Erreur des outils Éditeur de liens LNK1168
ms.date: 11/04/2016
f1_keywords:
- LNK1168
helpviewer_keywords:
- LNK1168
ms.assetid: 97ead151-fd99-46fe-9a1d-7e84dc0b8cc8
ms.openlocfilehash: 692bfbcc744307f32c8017b41ec27f5f421ea17c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253492"
---
# <a name="linker-tools-error-lnk1168"></a>Erreur des outils Éditeur de liens LNK1168

impossible d'ouvrir nomfichier en écriture

L'éditeur de liens ne peut pas écrire dans `filename`. Il est possible que le fichier soit utilisé et que son handle de fichier soit verrouillé par un autre processus. Il est possible également que vous ne disposiez pas de l'autorisation d'accès en écriture pour le fichier, ou pour le répertoire ou le partage réseau dans lequel il est situé. Cette erreur est souvent due à une condition transitoire, par exemple, un verrou détenu par un programme antivirus, un processus d’indexation de recherche de fichiers ou un retard dans la libération d’un verrou détenu par le système de génération Visual Studio.

Pour résoudre ce problème, vérifiez que le handle de fichier de `filename` n'est pas verrouillé, et que vous disposez d'une autorisation d'accès en écriture pour le fichier. S'il s'agit d'un exécutable, vérifiez qu'il n'est pas déjà en cours d'exécution.

Vous pouvez utiliser les utilitaires Windows SysInternals [handle](/sysinternals/downloads/handle) ou [Process Explorer](/sysinternals/downloads/process-explorer) pour déterminer sur quel processus un verrou de descripteur de fichier est défini `filename` . Vous pouvez également utiliser Process Explorer pour libérer les verrous des handles de fichiers ouverts. Pour plus d'informations sur l'utilisation de ces utilitaires, consultez les fichiers d'aide qui les accompagnent.

Si le fichier est verrouillé par un antivirus, vous pouvez résoudre ce problème en excluant les répertoires de sortie de génération de l'analyse automatique de l'antivirus. Les scanners antivirus sont souvent déclenchés par la création de fichiers dans le système de fichiers. Par ailleurs, ils verrouillent les fichiers pendant l‘analyse. Consultez la documentation de votre antivirus pour plus d'informations sur la façon d'exclure des répertoires spécifiques de l'analyse.

Si le fichier est verrouillé par un service d'indexation de la recherche, vous pouvez résoudre ce problème en excluant les répertoires de sortie de génération de l'indexation automatique. Consultez la documentation du service d'indexation pour plus d'informations. Pour modifier le service d’indexation de Windows Search, utilisez les **options d’indexation** dans le **panneau de configuration** Windows. Pour plus d’informations, consultez [index de recherche dans Windows 10 : Forum aux questions](https://support.microsoft.com/help/4098843/windows-10-search-indexing-faq).

Si votre exécutable ne peut pas être remplacé par le processus de génération, cela signifie qu'il est peut-être verrouillé par l'Explorateur de fichiers. Si le service d’expérience de l' **application** a été désactivé, l’Explorateur de fichiers peut conserver un verrou de handle de fichier exécutable pendant une période prolongée. Pour résoudre ce problème, exécutez **services. msc** , puis ouvrez la boîte de dialogue **Propriétés** pour le service **expérience d’application** . Remplacez le **type** de démarrage **désactivé** par **Manuel**.
