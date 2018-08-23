---
title: Deferrableeventargs, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8a53e33d55ccfac7eff763e53240295ea9b7b2a1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600969"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs, classe

Classe de modèle utilisée pour les types d’arguments des événements différés.

## <a name="syntax"></a>Syntaxe

```cpp
template <
typename TEventArgsInterface,
typename TEventArgsClass
>
class DeferrableEventArgs : public TEventArgsInterface
```

### <a name="parameters"></a>Paramètres

*TEventArgsInterface*  
Type d’interface qui déclare les arguments d’un événement différé.

*TEventArgsClass*  
La classe qui implémente *TEventArgsInterface*.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[DeferrableEventArgs::GetDeferral, méthode](../windows/deferrableeventargs-getdeferral-method.md)|Obtient une référence à la [report](http://go.microsoft.com/fwlink/p/?linkid=526520) objet qui représente un événement différé.|
|[DeferrableEventArgs::InvokeAllFinished, méthode](../windows/deferrableeventargs-invokeallfinished-method.md)|Appelé pour indiquer que le traitement d'un événement différé est terminé.|

## <a name="remarks"></a>Notes

Les instances de cette classe sont passées aux gestionnaires des événements différés. Les paramètres du modèle représentent une interface qui définit les détails des arguments d'événement pour un type spécifique d'événement différé, et une classe qui implémente cette interface.

La classe est présentée comme premier argument au gestionnaire d’événements qui traite l’événement différé. Vous pouvez appeler la [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) méthode pour obtenir le [report](http://go.microsoft.com/fwlink/p/?linkid=526520) objet à partir de laquelle vous pouvez obtenir toutes les informations relatives à l’événement différé. Une fois la gestion des événements terminée, vous devez appeler Complete sur l'objet Deferral. Vous devez appeler [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md) à la fin de la méthode de gestionnaire d’événements, ce qui garantit que l’achèvement de tous les événements différés est communiqué correctement.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)