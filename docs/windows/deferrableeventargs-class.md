---
title: Deferrableeventargs, classe | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 082cae10bbd01c4c46fcfaa84bfd94ba6178bc1a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401782"
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

*TEventArgsInterface*<br/>
Type d’interface qui déclare les arguments d’un événement différé.

*TEventArgsClass*<br/>
La classe qui implémente *TEventArgsInterface*.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

Nom                                                         | Description
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[DeferrableEventArgs::GetDeferral](#getdeferral)             | Obtient une référence à la [report](http://go.microsoft.com/fwlink/p/?linkid=526520) objet qui représente un événement différé.
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | Appelé pour indiquer que le traitement d'un événement différé est terminé.

## <a name="remarks"></a>Notes

Les instances de cette classe sont passées aux gestionnaires des événements différés. Les paramètres du modèle représentent une interface qui définit les détails des arguments d'événement pour un type spécifique d'événement différé, et une classe qui implémente cette interface.

La classe est présentée comme premier argument au gestionnaire d’événements qui traite l’événement différé. Vous pouvez appeler la [GetDeferral](#getdeferral) méthode pour obtenir le [report](http://go.microsoft.com/fwlink/p/?linkid=526520) objet à partir de laquelle vous pouvez obtenir toutes les informations relatives à l’événement différé. Une fois la gestion des événements terminée, vous devez appeler Complete sur l'objet Deferral. Vous devez appeler [InvokeAllFinished](#invokeallfinished) à la fin de la méthode de gestionnaire d’événements, ce qui garantit que l’achèvement de tous les événements différés est communiqué correctement.

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::WRL

## <a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

Obtient une référence à la [report](http://go.microsoft.com/fwlink/p/?linkid=526520) objet qui représente un événement différé.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```

### <a name="parameters"></a>Paramètres

*Résultat*<br/>
Un pointeur qui référence le [report](http://go.microsoft.com/fwlink/p/?linkid=526520) lors de la fin de l’appel de l’objet.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

Appelé pour indiquer que le traitement d'un événement différé est terminé.
  
```cpp
void InvokeAllFinished()  
```
  
### <a name="remarks"></a>Notes

Vous devez appeler cette méthode après les appels de source d’événement [InvokeAll](../windows/eventsource-invokeall-method.md). L'appel à cette méthode empêche tout autre report et force l'exécution du gestionnaire d'achèvement en l'absence de report.
