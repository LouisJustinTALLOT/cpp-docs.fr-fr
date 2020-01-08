---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: 37bb7a8c7fef963f340704561e24e33cc36707f3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298634"
---
# <a name="queryinterface"></a>QueryInterface

Bien qu’il existe des mécanismes permettant à un objet d’exprimer les fonctionnalités qu’il fournit de manière statique (avant qu’il ne soit instancié), le mécanisme COM fondamental consiste à utiliser la méthode `IUnknown` appelée [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

Chaque interface est dérivée de `IUnknown`, donc chaque interface a une implémentation de `QueryInterface`. Quelle que soit l’implémentation, cette méthode interroge un objet à l’aide de l’IID de l’interface à laquelle l’appelant souhaite obtenir un pointeur. Si l’objet prend en charge cette interface, `QueryInterface` récupère un pointeur vers l’interface, tout en appelant également `AddRef`. Sinon, elle retourne le code d’erreur E_NOINTERFACE.

Notez que vous devez respecter les règles de [décompte de références](../atl/reference-counting.md) à tout moment. Si vous appelez `Release` sur un pointeur d’interface pour décrémenter le décompte de références à zéro, vous ne devez pas utiliser à nouveau ce pointeur. Parfois, vous devrez peut-être obtenir une référence faible à un objet (autrement dit, vous souhaiterez peut-être obtenir un pointeur vers l’une de ses interfaces sans incrémenter le nombre de références), mais il n’est pas acceptable de le faire en appelant `QueryInterface` suivi de `Release`. Le pointeur obtenu de cette manière n’est pas valide et ne doit pas être utilisé. Cela devient plus facilement visible lorsque [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) est défini, donc la définition de cette macro est un moyen pratique de rechercher des bogues de comptage de références.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[QueryInterface : navigation dans un objet](/windows/win32/com/queryinterface--navigating-in-an-object)
