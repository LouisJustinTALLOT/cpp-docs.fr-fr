---
title: Gestion des erreurs (CRT)
ms.date: 11/04/2016
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
ms.openlocfilehash: d38aaf76a4901b12290782957db90049d815d278
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443323"
---
# <a name="error-handling-crt"></a>Gestion des erreurs (CRT)

Utilisez ces routines pour gérer les erreurs de programme.

## <a name="error-handling-routines"></a>Routines de gestion des erreurs

|Routine|Utilisation|
|-------------|---------|
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md), macro|Vérifier les erreurs logiques de programmation ; disponible dans les versions Release et Debug de la bibliothèque runtime.|
|[_ASSERT, _ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), macros|Similaire à **assert**, mais uniquement disponible dans les versions Debug de la bibliothèque Runtime.|
|[clearerr](../c-runtime-library/reference/clearerr.md)|Réinitialiser l’indicateur d’erreur. L’appel de **rewind** ou la fermeture d’un flux réinitialise également l’indicateur d’erreur.|
|[_eof](../c-runtime-library/reference/eof.md)|Vérifier la fin du fichier dans les E/S de bas niveau.|
|[feof](../c-runtime-library/reference/feof.md)|Vérifier la fin du fichier. La fin du fichier est également indiquée quand **_read** retourne la valeur 0.|
|[ferror](../c-runtime-library/reference/ferror.md)|Vérifier les erreurs d’E/S du flux.|
|[_RPT, _RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md), macros|Générer un rapport similaire à **printf**, mais uniquement disponible dans les versions Debug de la bibliothèque Runtime.|
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|Modifie **__error_mode** pour déterminer un emplacement autre que celui utilisé par défaut dans lequel le Runtime C écrit un message d’erreur pour une erreur qui risque de mettre fin au programme.|
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|Définit le gestionnaire pour un appel de fonction virtuelle pure.|

## <a name="see-also"></a>Voir aussi

- [Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)
