---
description: 'En savoir plus sur : classe ICommandTextImpl'
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
ms.openlocfilehash: 4b48b9f8f2ee535a648681064cc6b1083c76e489
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287370"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl, classe

Fournit une implémentation pour l’interface [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Classe de commande dérivée de `ICommandTextImpl` .

## <a name="requirements"></a>Spécifications

**En-tête :** altdb. h

## <a name="members"></a>Membres

### <a name="interface-methods"></a>Méthodes d'interface

| Nom | Description |
|-|-|
|[GetCommandText](#getcommandtext)|Retourne la commande de texte définie par le dernier appel à [SetCommandText](#setcommandtext).|
|[SetCommandText](#setcommandtext)|Définit le texte de la commande, en remplaçant le texte de la commande existante.|

### <a name="data-members"></a>Données membres

| Nom | Description |
|-|-|
|[m_strCommandText](#strcommandtext)|Stocke le texte de la commande.|

## <a name="remarks"></a>Notes

Interface obligatoire sur les commandes.

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a> ICommandTextImpl :: GetCommandText

Retourne la commande de texte définie par le dernier appel à [SetCommandText](#setcommandtext).

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandText :: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*. Le paramètre *pguidDialect* est ignoré par défaut.

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a> ICommandTextImpl :: SetCommandText

Définit le texte de la commande, en remplaçant le texte de la commande existante.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>Paramètres

Consultez [ICommandText :: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) dans le *Guide de référence du programmeur OLE DB*.

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a> ICommandTextImpl :: m_strCommandText

Stocke la chaîne de texte de la commande.

### <a name="syntax"></a>Syntaxe

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>Voir aussi

[Modèles du fournisseur OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architecture du modèle de fournisseur OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
