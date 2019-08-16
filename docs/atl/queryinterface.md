---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: de2762cff3d697261e159336d866a5a7cb10fafa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492002"
---
# <a name="queryinterface"></a>QueryInterface

Bien qu’il existe des mécanismes permettant à un objet d’exprimer les fonctionnalités qu’il fournit de manière statique (avant qu’il ne soit instancié), le mécanisme com `IUnknown` fondamental consiste à utiliser la méthode appelée [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

Chaque interface est dérivée `IUnknown`de, donc chaque interface a une implémentation `QueryInterface`de. Quelle que soit l’implémentation, cette méthode interroge un objet à l’aide de l’IID de l’interface à laquelle l’appelant souhaite obtenir un pointeur. Si l’objet prend en charge cette `QueryInterface` interface, récupère un pointeur vers l’interface, tout en `AddRef`appelant également. Dans le cas contraire, elle retourne le code d’erreur E_NOINTERFACE.

Notez que vous devez respecter les règles de décompte de [références](../atl/reference-counting.md) à tout moment. Si vous appelez `Release` sur un pointeur d’interface pour décrémenter le décompte de références à zéro, vous ne devez pas utiliser à nouveau ce pointeur. Parfois, vous devrez peut-être obtenir une référence faible à un objet (autrement dit, vous souhaiterez peut-être obtenir un pointeur vers l’une de ses interfaces sans incrémenter le nombre de références), mais il n’est `QueryInterface` pas acceptable `Release`d’appeler suivi de. Le pointeur obtenu de cette manière n’est pas valide et ne doit pas être utilisé. Cela devient plus facilement visible quand [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) est défini. par conséquent, la définition de cette macro est un moyen pratique de rechercher des bogues de comptage de références.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[Appels Navigation dans un objet](/windows/win32/com/queryinterface--navigating-in-an-object)
