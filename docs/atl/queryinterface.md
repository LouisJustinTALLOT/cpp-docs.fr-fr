---
title: QueryInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3227ebd4767bd7639bb5e5d8d5a1c73e26079dc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953419"
---
# <a name="queryinterface"></a>QueryInterface
Bien qu’il existe des mécanismes par lesquels un objet peut exprimer la fonctionnalité qu’elle fournit statiquement (avant son instanciation), le mécanisme fondamental de COM consiste à utiliser le `IUnknown` méthode appelée [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Chaque interface est dérivée de `IUnknown`, chaque interface a une implémentation de `QueryInterface`. Quel que soit l’implémentation, cette méthode interroge un objet à l’aide de l’IID de l’interface à laquelle l’appelant veut un pointeur. Si l’objet prend en charge cette interface, `QueryInterface` récupère un pointeur vers l’interface, tout en appelant également `AddRef`. Sinon, elle retourne le code d’erreur E_NOINTERFACE.  
  
 Notez que vous devez respecter [décompte](../atl/reference-counting.md) règles à tout moment. Si vous appelez `Release` sur un pointeur d’interface pour décrémenter le décompte de références à zéro, vous ne devriez utiliser ce pointeur à nouveau. Parfois, vous devrez peut-être obtenir une référence faible à un objet (autrement dit, vous pouvez obtenir un pointeur vers une de ses interfaces sans incrémenter le décompte de références), mais il n’est pas acceptable pour ce faire, appelez `QueryInterface` suivie `Release`. Le pointeur obtenu de cette manière n’est pas valide et ne doit pas être utilisé. Cela devient évident lorsque [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) est défini, afin de définir cette macro est un moyen utile de bogues de comptage de références de recherche.  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à COM](../atl/introduction-to-com.md)   
 [QueryInterface : Navigation dans un objet](http://msdn.microsoft.com/library/windows/desktop/ms687230)

