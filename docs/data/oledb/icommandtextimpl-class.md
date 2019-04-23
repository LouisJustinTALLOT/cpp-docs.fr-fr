---
title: ICommandTextImpl, classe
ms.date: 11/04/2016
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: de9e930056db7b91968ca1ce471a87809693376a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037102"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl, classe

Fournit une implémentation pour le [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) interface.

## <a name="syntax"></a>Syntaxe

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Dérivé de la classe de commande `ICommandTextImpl`.

## <a name="requirements"></a>Configuration requise

**En-tête :** altdb.h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d’interface

|||
|-|-|
|[GetCommandText](#getcommandtext)|Retourne la commande de texte définie par le dernier appel à [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).|
|[SetCommandText](#setcommandtext)|Définit le texte de commande, en remplaçant le texte de commande existant.|

### <a name="data-members"></a>Membres de données

|||
|-|-|
|[m_strCommandText](#strcommandtext)|Stocke le texte de commande.|

## <a name="remarks"></a>Notes

Une interface obligatoire sur les commandes.

## <a name="getcommandtext"></a> ICommandTextImpl::GetCommandText

Retourne la commande de texte définie par le dernier appel à [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) dans le *de référence du programmeur OLE DB*. Le *pguidDialect* paramètre est ignoré par défaut.

## <a name="setcommandtext"></a> ICommandTextImpl::SetCommandText

Définit le texte de commande, en remplaçant le texte de commande existant.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) dans le *de référence du programmeur OLE DB*.

## <a name="strcommandtext"></a> ICommandTextImpl::m_strCommandText

Stocke la chaîne de texte de commande.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture des modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)