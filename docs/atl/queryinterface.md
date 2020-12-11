---
description: 'En savoir plus sur : QueryInterface'
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: b22163c9e69bd5573f8e6060df0457862813c366
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159165"
---
# <a name="queryinterface"></a>QueryInterface

Bien qu’il existe des mécanismes permettant à un objet d’exprimer les fonctionnalités qu’il fournit de manière statique (avant qu’il ne soit instancié), le mécanisme COM fondamental consiste à utiliser la `IUnknown` méthode appelée [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

Chaque interface est dérivée de `IUnknown` , donc chaque interface a une implémentation de `QueryInterface` . Quelle que soit l’implémentation, cette méthode interroge un objet à l’aide de l’IID de l’interface à laquelle l’appelant souhaite obtenir un pointeur. Si l’objet prend en charge cette interface, `QueryInterface` récupère un pointeur vers l’interface, tout en appelant également `AddRef` . Sinon, elle retourne le code d’erreur E_NOINTERFACE.

Notez que vous devez respecter les règles de [décompte de références](../atl/reference-counting.md) à tout moment. Si vous appelez `Release` sur un pointeur d’interface pour décrémenter le décompte de références à zéro, vous ne devez pas utiliser à nouveau ce pointeur. Parfois, vous devrez peut-être obtenir une référence faible à un objet (autrement dit, vous souhaiterez peut-être obtenir un pointeur vers l’une de ses interfaces sans incrémenter le nombre de références), mais il n’est pas acceptable d’appeler `QueryInterface` suivi de `Release` . Le pointeur obtenu de cette manière n’est pas valide et ne doit pas être utilisé. Cela devient plus facilement visible lorsque [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) est défini, donc la définition de cette macro est un moyen pratique de rechercher des bogues de comptage de références.

## <a name="see-also"></a>Voir aussi

[Introduction à COM](../atl/introduction-to-com.md)<br/>
[QueryInterface : navigation dans un objet](/windows/win32/com/queryinterface--navigating-in-an-object)
