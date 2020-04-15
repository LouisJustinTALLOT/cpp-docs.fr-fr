---
title: Options de lien
ms.date: 11/04/2016
helpviewer_keywords:
- nothrownew.obj
- newmode.obj
- noenv.obj
- psetargv.obj
- legacy_stdio_float_rounding.obj
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
ms.openlocfilehash: ea71faab639a8c0a09d6e332618dd7e09159a4e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351104"
---
# <a name="link-options"></a>Options de lien

Le répertoire de la bibliothèque CRT inclut plusieurs petits fichiers objets qui activent des fonctions CRT spécifiques sans aucune modification de code. Ceux-ci sont appelés « options de lien », car il suffit de les ajouter à la ligne de commande de l’éditeur de liens pour les utiliser.

Les versions CLR en mode pur de ces objets sont déconseillées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017. Utilisez les versions standards pour le code natif et /clr.

|Natif et /clr|Mode pur|Description|
|----------------------|---------------|-----------------|
|binmode.obj|pbinmode.obj|Définit le mode binaire de traduction de fichiers par défaut. Consultez [_fmode](../c-runtime-library/fmode.md).|
|chkstk.obj|n/a|Assure la vérification de la pile et la prise en charge de l’allocation quand la bibliothèque CRT n’est pas utilisée.|
|commode.obj|pcommode.obj|Définit l’indicateur de validation global sur « Valider ». Consultez [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) et [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|
|exe_initialize_mta.lib|n/a|Initialise le cloisonnement MTA durant le démarrage d’EXE, ce qui permet d’utiliser des objets COM dans des pointeurs intelligents globaux. Du fait que cette option divulgue une référence au cloisonnement MTA durant l’arrêt, ne l’utilisez pas pour les DLL. L’établissement d’une liaison à ce fichier revient à inclure combase.h et à définir _EXE_INITIALIZE_MTA. |
|fp10.obj|n/a|Remplace le contrôle de précision par défaut par 64 bits. Consultez [Prise en charge de la virgule flottante](../c-runtime-library/floating-point-support.md).|
|invalidcontinue.obj|pinvalidcontinue.obj|Définit un gestionnaire de paramètre non valide par défaut qui ne fait rien, ce qui signifie que les paramètres non valides passés aux fonctions CRT définissent simplement errno et retournent un résultat d’erreur.|
|legacy_stdio_float_rounding.obj|n/a|L’impression de valeurs à points flottants (par exemple, lors de [l’utilisation de l’impression)](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)avec le Windows 10 19041 Universal C Runtime a été corrigée. Il arrondit maintenant correctement exactement representable des nombres de points flottants, et respecte l’arrondissement de points flottants demandé par [fesetenv](../c-runtime-library/reference/fesetenv1.md). Cette mise à jour du comportement est disponible dans Visual Studio 2019 version 16.2 et plus tard. Le comportement hérité est utilisé dans les versions antérieures de Visual Studio, ou en fournissant cette option de lien.|
|loosefpmath.obj|n/a|Garantit la tolérance de valeurs anormales par le code à virgule flottante.|
|newmode.obj|pnewmode.obj|Entraîne l’appel par [malloc](../c-runtime-library/reference/malloc.md) du nouveau gestionnaire en cas d’échec. Consultez [_set_new_mode](../c-runtime-library/reference/set-new-mode.md), [_set_new_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md) et [realloc](../c-runtime-library/reference/realloc.md).|
|noarg.obj|pnoarg.obj|Désactive tout le traitement d’argc et d’argv.|
|nochkclr.obj|n/a|Ne fait rien. Supprime de votre projet.|
|noenv.obj|pnoenv.obj|Désactive la création d’un environnement mis en cache pour la bibliothèque CRT.|
|nothrownew.obj|pnothrownew.obj|Active la version qui ne peut pas être levée de l’opérateur new dans la bibliothèque CRT. Consultez [Opérateurs new et delete](../cpp/new-and-delete-operators.md).|
|setargv.obj|psetargv.obj|Active le développement des caractères génériques dans les arguments de ligne de commande. Consultez [Développement des arguments avec caractères génériques](../c-language/expanding-wildcard-arguments.md).|
|threadlocale.obj|pthreadlocale.obj|Active des paramètres régionaux par thread pour tous les nouveaux threads par défaut.|
|wsetargv.obj|pwsetargv.obj|Active le développement des caractères génériques dans les arguments de ligne de commande. Consultez [Développement des arguments avec caractères génériques](../c-language/expanding-wildcard-arguments.md).|

## <a name="see-also"></a>Voir aussi

- [Caractéristiques de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
