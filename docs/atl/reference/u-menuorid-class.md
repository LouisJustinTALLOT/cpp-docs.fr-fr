---
title: _U_menuorid, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_MENUorID
- ATL::_U_MENUorID
- _U_MENUorID
dev_langs:
- C++
helpviewer_keywords:
- U_MENUorID class
- _U_MENUorID class
ms.assetid: cfc8032b-61b4-4a68-ba3a-92b82500ccae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 333bdbd88d554e3fe3e3f233ce9968df75d73dfc
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690888"
---
# <a name="umenuorid-class"></a>_U_menuorid, classe
Cette classe fournit des wrappers pour `CreateWindow` et `CreateWindowEx`.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class _U_MENUorID
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[_U_MENUorID::_U_MENUorID](#_u_menuorid___u_menuorid)|Constructeur.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[_U_MENUorID::m_hMenu](#_u_menuorid__m_hmenu)|Un handle à un menu.|  
  
## <a name="remarks"></a>Notes  
 Cette classe d’adaptateur argument permet ID (ventes) ou handles de menu (HMENUs) à passer à une fonction sans nécessiter un cast explicite part de l’appelant.  
  
 Cette classe est conçue pour l’implémentation des wrappers pour l’API Windows, en particulier le [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) et [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) fonctions, qui acceptent un argument HMENU qui peut être une fenêtre enfant identificateur (UINT) plutôt qu’un handle de menu. Par exemple, vous pouvez voir cette classe en cours d’utilisation en tant que paramètre à [CWindowImpl::Create](cwindowimpl-class.md#create).  

  
 La classe définit deux surcharges de constructeur : une accepte un argument UINT et l’autre accepte un argument HMENU. L’argument UINT est simplement casté en une valeur HMENU du constructeur et le résultat stocké dans le membre de données unique de la classe, [m_hMenu](#_u_menuorid__m_hmenu). L’argument au constructeur HMENU est stocké directement, sans conversion.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlwin.h  
  
##  <a name="_u_menuorid__m_hmenu"></a>  _U_MENUorID::m_hMenu  
 La classe contient la valeur passée à un de ses constructeurs comme un membre de données public HMENU.  
  
```
HMENU m_hMenu;
```  
  
##  <a name="_u_menuorid___u_menuorid"></a>  _U_MENUorID::_U_MENUorID  
 L’argument UINT est simplement casté en une valeur HMENU du constructeur et le résultat stocké dans le membre de données unique de la classe, [m_hMenu](#_u_menuorid__m_hmenu).  
  
```
_U_MENUorID(UINT nID);  
_U_MENUorID(HMENU hMenu);
```  
  
### <a name="parameters"></a>Paramètres  
 *nID*  
 Un identificateur de fenêtre enfant.  
  
 *hMenu*  
 Un handle de menu.  
  
### <a name="remarks"></a>Notes  
 L’argument au constructeur HMENU est stocké directement, sans conversion.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
