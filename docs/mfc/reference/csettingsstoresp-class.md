---
title: Classe de CSettingsStoreSP | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7cf9659b6c367146a565834bd65fdfc9f28a9812
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="csettingsstoresp-class"></a>Classe de CSettingsStoreSP
Le `CSettingsStoreSP` est une classe d’assistance que vous pouvez utiliser pour créer des instances de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSettingsStoreSP  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Construit un objet `CSettingsStoreSP`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSettingsStoreSP::Create](#create)|Crée une instance d’une classe qui est dérivée de `CSettingsStore`.|  
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Définit la classe d’exécution. Le `Create` méthode utilise la classe d’exécution pour déterminer quelle classe d’objets à créer.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|`m_dwUserData`|Les données utilisateur personnalisées qui sont stockées dans le `CSettingsStoreSP` objet. Vous fournissez ces données dans le constructeur de la `CSettingsStoreSP` objet.|  
|`m_pRegistry`|Le `CSettingsStore`-dérivée de l’objet qui le `Create` méthode crée.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la `CSettingsStoreSP` classe pour rediriger toutes les opérations de Registre MFC à d’autres emplacements, comme un fichier XML ou une base de données. Pour cela, procédez comme suit :  
  
1.  Créer une classe (tel que `CMyStore`) et de la dériver de `CSettingsStore`.  
  
2.  Utilisez [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) et [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) macros avec votre personnalisé `CSettingsStore` classe pour permettre la création dynamique.  
  
3.  Substituer des fonctions virtuelles et d’implémenter le `Read` et `Write` fonctions dans votre classe personnalisée. Implémenter d’autres fonctionnalités pour lire et écrire des données dans l’emplacement souhaité.  
  
4.  Dans votre application, appelez `CSettingsStoreSP::SetRuntimeClass` et passez un pointeur vers le [CRuntimeClass Structure](../../mfc/reference/cruntimeclass-structure.md) obtenues à partir de votre classe.  
  
 Chaque fois que le framework accèdent en général le Registre, il va maintenant dynamiquement instancier votre classe personnalisée et l’utiliser pour lire ou écrire des données.  
  
 `CSettingsStoreSP::SetRuntimeClass`utilise une variable statique globale. Par conséquent, qu’un seul magasin personnalisé est disponible à la fois.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxsettingsstore.h  
  
##  <a name="create"></a>CSettingsStoreSP::Create  
 Crée une instance d’un objet qui est dérivé de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).  
  
```  
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,  
    BOOL bReadOnly);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bAdmin`  
 Un paramètre booléen qui détermine si un `CSettingsStore` objet est créé en mode administrateur.  
  
 [in] `bReadOnly`  
 Un paramètre booléen qui détermine si un `CSettingsStore` objet est créé pour l’accès en lecture seule.  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à la nouvelle `CSettingsStore` objet.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser la méthode [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) pour déterminer le type d’objet `CSettingsStoreSP::Create` va créer. Par défaut, cette méthode crée un `CSettingsStore` objet.  
  
 Si vous créez un `CSettingsStore` de l’objet en mode administrateur, l’emplacement par défaut pour tous les accès de Registre est HKEY_LOCAL_MACHINE. Sinon, l’emplacement par défaut pour tous les accès de Registre est HKEY_CURRENT_USER.  
  
 Si `bAdmin` est `TRUE`, l’application doit disposer des droits d’administration. Dans le cas contraire, il échoue lorsqu’il tente d’accéder au Registre.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `Create` méthode de la `CSettingsStoreSP` classe.  
  
 [!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]  
  
##  <a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP  
 Construit un [CSettingsStoreSP classe](../../mfc/reference/csettingsstoresp-class.md) objet.  
  
```  
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `dwUserData`  
 Défini par l’utilisateur qui le `CSettingsStoreSP` stocke l’objet.  
  
### <a name="remarks"></a>Notes  
 Le `CSettingsStoreSP` objet stocke les données à partir de `dwUserData` dans la variable membre protégé `m_dwUserData`.  
  
##  <a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass  
 Définit la classe d’exécution. La méthode [CSettingsStoreSP::Create](#create) utilise la classe d’exécution pour déterminer le type d’objet à créer.  
  
```  
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pRTI`  
 Un pointeur vers les informations de classe runtime pour une classe dérivée de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`en cas de réussite ; `FALSE` si la classe identifiée par `pRTI` n’est pas dérivée de `CSettingsStore`.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez utiliser la [CSettingsStoreSP classe](../../mfc/reference/csettingsstoresp-class.md) pour dériver des classes de `CSettingsStore`. Utilisez la méthode `SetRuntimeClass` si vous souhaitez créer des objets d’une classe personnalisée dérivée de `CSettingsStore`.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CSettingsStore, classe](../../mfc/reference/csettingsstore-class.md)
