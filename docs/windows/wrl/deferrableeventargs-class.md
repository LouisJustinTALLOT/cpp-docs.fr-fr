---
title: DeferrableEventArgs, classe
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: 4a3786e65873d6837389ad4fa5e7d06a14d66460
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278357"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs, classe

Classe de modèle utilisée pour les types d'arguments des événements différés.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
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
[DeferrableEventArgs::GetDeferral](#getdeferral)             | Obtient une référence à la [report](/uwp/api/windows.foundation.deferral) objet qui représente un événement différé.
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | Appelée pour indiquer que toutes les opérations de traitement d'un événement différé sont terminées.

## <a name="remarks"></a>Notes

Les instances de cette classe sont passées aux gestionnaires des événements différés. Les paramètres du modèle représentent une interface qui définit les détails des arguments d’événement pour un type spécifique d’événement différé, et une classe qui implémente cette interface.

La classe est présentée comme premier argument au gestionnaire d'événements qui traite l'événement différé. Vous pouvez appeler la [GetDeferral](#getdeferral) méthode pour obtenir le [report](/uwp/api/windows.foundation.deferral) objet à partir de laquelle vous pouvez obtenir toutes les informations relatives à l’événement différé. Une fois la gestion des événements terminée, vous devez appeler Complete sur l'objet Deferral. Vous devez appeler [InvokeAllFinished](#invokeallfinished) à la fin de la méthode de gestionnaire d’événements, ce qui garantit que l’achèvement de tous les événements différés est communiqué correctement.

## <a name="requirements"></a>Spécifications

**En-tête :** event.h

**Espace de noms :** Microsoft::wrl

## <a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

Obtient une référence à la [report](/uwp/api/windows.foundation.deferral) objet qui représente un événement différé.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>Paramètres

*result*<br/>
Un pointeur qui référence le [report](/uwp/api/windows.foundation.deferral) lors de la fin de l’appel de l’objet.

### <a name="return-value"></a>Valeur de retour

S_OK si l'opération réussit. Sinon, une valeur HRESULT indique l'erreur.

## <a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

Appelée pour indiquer que toutes les opérations de traitement d'un événement différé sont terminées.

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Notes

Vous devez appeler cette méthode après les appels de source d’événement [InvokeAll](eventsource-class.md#invokeall). L'appel à cette méthode empêche tout autre report et force l'exécution du gestionnaire d'achèvement en l'absence de report.
