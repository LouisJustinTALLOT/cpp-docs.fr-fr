---
title: Options de lien
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- loosefpmath.obj
- smallheap.obj
- fp10.obj
- nochkclr.obj
- chkstk.obj
- pcommode.obj
- pnoenv.obj
- link options [C++]
- invalidcontinue.obj
- pnothrownew.obj
- pwsetargv.obj
- pinvalidcontinue.obj
- wsetargv.obj
- binmode.obj
- setargv.obj
- noarg.obj
- pnewmode.obj
- commode.obj
- pthreadlocale.obj
- pbinmode.obj
- threadlocale.obj
- pnoarg.obj
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
ms.openlocfilehash: 8cd5513acd2617e784b2ec9fa203614b752e6076
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661823"
---
# <a name="link-options"></a>Options de lien

Le répertoire de la bibliothèque CRT inclut plusieurs petits fichiers objets qui activent des fonctions CRT spécifiques sans aucune modification de code. Ceux-ci sont appelés « options de lien », car il suffit de les ajouter à la ligne de commande de l’éditeur de liens pour les utiliser.

Les versions CLR en mode pur de ces objets sont déconseillées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017. Utilisez les versions standards pour le code natif et /clr.

|Natif et /clr|Mode pur|Description|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Définit le mode binaire de traduction de fichiers par défaut. Consultez [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|N/A|Assure la vérification de la pile et la prise en charge de l’allocation quand la bibliothèque CRT n’est pas utilisée.|
|commode.obj|pcommode.obj|Définit l’indicateur de validation global sur « Valider ». Consultez [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) et [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|N/A|Initialise le cloisonnement MTA durant le démarrage d’EXE, ce qui permet d’utiliser des objets COM dans des pointeurs intelligents globaux. Du fait que cette option divulgue une référence au cloisonnement MTA durant l’arrêt, ne l’utilisez pas pour les DLL. L’établissement d’une liaison à ce fichier revient à inclure combase.h et à définir _EXE_INITIALIZE_MTA. |
|fp10.obj|N/A|Remplace le contrôle de précision par défaut par 64 bits. Consultez [Prise en charge de la virgule flottante](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Définit un gestionnaire de paramètre non valide par défaut qui ne fait rien, ce qui signifie que les paramètres non valides passés aux fonctions CRT définissent simplement errno et retournent un résultat d’erreur.|
|loosefpmath.obj|N/A|Garantit la tolérance de valeurs anormales par le code à virgule flottante.|
|newmode.obj|pnewmode.obj|Entraîne l’appel par [malloc](../c-runtime-library/reference/malloc.md) du nouveau gestionnaire en cas d’échec. Consultez [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md) et [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Désactive tout le traitement d’argc et d’argv.|
|nochkclr.obj|N/A|Sans effet Supprime de votre projet.|
|noenv.obj|pnoenv.obj|Désactive la création d’un environnement mis en cache pour la bibliothèque CRT.|
|nothrownew.obj|pnothrownew.obj|Active la version qui ne peut pas être levée de l’opérateur new dans la bibliothèque CRT. Consultez [Opérateurs new et delete](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Active le développement des caractères génériques dans les arguments de ligne de commande. Consultez [Développement des arguments avec caractères génériques](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Active des paramètres régionaux par thread pour tous les nouveaux threads par défaut.|
|wsetargv.obj|pwsetargv.obj|Active le développement des caractères génériques dans les arguments de ligne de commande. Consultez [Développement des arguments avec caractères génériques](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)
