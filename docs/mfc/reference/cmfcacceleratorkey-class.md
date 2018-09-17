---
title: Cmfcacceleratorkey, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7d87b7a2a76ea73989a9ab7dd845666625e91aa0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711592"
---
# <a name="cmfcacceleratorkey-class"></a>Cmfcacceleratorkey, classe
Une classe d’assistance qui implémente le mappage de clé virtuel et la mise en forme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Construit un objet `CMFCAcceleratorKey`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|Convertit la structure d’accélération à sa représentation visuelle.|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Définit la touche de raccourci pour le `CMFCAcceleratorKey` objet.|  
  
## <a name="remarks"></a>Notes  
 Touches accélérateur sont également appelées touches de raccourci. Si vous souhaitez afficher les raccourcis clavier entrées par un utilisateur, le [cmfcacceleratorkeyassignctrl, classe](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) maps raccourcis clavier, tels que Alt + Maj + S, dans un format de texte personnalisé, tel que « Alt + Maj + S ». Chaque `CMFCAcceleratorKey` objet mappe une touche de raccourci unique dans un format de texte.  
  
 Pour plus d’informations sur l’utilisation des touches de raccourci et les tables d’accélérateurs, consultez [ckeyboardmanager, classe](../../mfc/reference/ckeyboardmanager-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCAcceleratorKey` objet et comment utiliser son `Format` (méthode).  
  
 [!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxacceleratorkey.h  
  
##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey  
 Construit un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objet.  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Paramètres  
*lpAccel*<br/>
[in] Pointeur vers une touche de raccourci.  
  
### <a name="remarks"></a>Notes  
 Si vous ne fournissez pas une touche de raccourci lorsque vous créez un `CMFCAccleratorKey`, utilisez le [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) méthode pour associer une touche de raccourci avec votre `CMFCAcceleratorKey` objet.  
  
##  <a name="format"></a>  CMFCAcceleratorKey::Format  
 Convertit la structure d’accélération à sa valeur de chaîne associée.  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>Paramètres  
*str*<br/>
[out] Une référence à un `CString` objet dans lequel la méthode écrit la touche de raccourci traduite.  
  
### <a name="remarks"></a>Notes  
 Cette méthode récupère le format de chaîne de la touche de raccourci associé. Vous pouvez définir le format de chaîne d’un [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) de l’objet à l’aide du constructeur ou la méthode [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).  
  
##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator  
 Définit la touche de raccourci pour le [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) objet.  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>Paramètres  
*lpAccel*<br/>
[in] Pointeur vers une touche de raccourci.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour définir la touche de raccourci pour un `CMFCAcceleratorKey` si vous n’avez pas fourni une touche de raccourci lorsque vous avez créé le `CMFCAcceleratorKey`.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager, classe](../../mfc/reference/ckeyboardmanager-class.md)
