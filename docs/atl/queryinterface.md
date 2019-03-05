---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- QueryInterface
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: a3ec3c6e0d2b534c3af49000202461a43a65dae9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261460"
---
# <a name="queryinterface"></a>QueryInterface

Bien qu’il existe des mécanismes par lesquels un objet peut exprimer la fonctionnalité qu’elle fournit statiquement (avant son instanciation), le mécanisme fondamental de COM consiste à utiliser le `IUnknown` méthode appelée [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

Chaque interface est dérivée de `IUnknown`, chaque interface a une implémentation de `QueryInterface`. Quel que soit l’implémentation, cette méthode interroge un objet à l’aide de l’IID de l’interface à laquelle l’appelant veut un pointeur. Si l’objet prend en charge cette interface, `QueryInterface` récupère un pointeur vers l’interface, tout en appelant également `AddRef`. Sinon, elle retourne le code d’erreur E_NOINTERFACE.

Notez que vous devez respecter [décompte](../atl/reference-counting.md) règles à tout moment. Si vous appelez `Release` sur un pointeur d’interface pour décrémenter le décompte de références à zéro, vous ne devriez utiliser ce pointeur à nouveau. Parfois, vous devrez peut-être obtenir une référence faible à un objet (autrement dit, vous pouvez obtenir un pointeur vers une de ses interfaces sans incrémenter le décompte de références), mais il n’est pas acceptable pour ce faire, appelez `QueryInterface` suivie `Release`. Le pointeur obtenu de cette manière n’est pas valide et ne doit pas être utilisé. Cela devient évident lorsque [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) est défini, afin de définir cette macro est un moyen utile de bogues de comptage de références de recherche.

## <a name="see-also"></a>Voir aussi

[Présentation de COM](../atl/introduction-to-com.md)<br/>
[QueryInterface : Navigation dans un objet](/windows/desktop/com/queryinterface--navigating-in-an-object)
