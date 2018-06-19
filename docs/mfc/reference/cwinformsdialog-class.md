---
title: Classe de CWinFormsDialog | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7596140f48b62a63189444bee6fb363552766fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371557"
---
# <a name="cwinformsdialog-class"></a>Classe de CWinFormsDialog
Wrapper pour une classe de boîte de dialogue MFC qui héberge un contrôle utilisateur Windows Forms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
    public CDialog  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TManagedControl`  
 Le contrôle utilisateur .NET Framework, à afficher dans l’application MFC.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Construit un objet `CWinFormsDialog`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|Récupère une référence au contrôle utilisateur Windows Forms.|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Récupère un handle de fenêtre pour le contrôle utilisateur Windows Forms.|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Initialise la boîte de dialogue MFC par la création et l’hébergement d’un contrôle utilisateur Windows Forms.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Name||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|Remplace [CWinFormsDialog::GetControl](#getcontrol) dans les expressions.|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|Convertit un type en tant que référence à un contrôle utilisateur Windows Forms.|  
  
## <a name="remarks"></a>Notes  
 `CWinFormsDialog` est un wrapper pour une classe de boîte de dialogue MFC ( [CDialog](../../mfc/reference/cdialog-class.md)) qui héberge un contrôle utilisateur Windows Forms. Cela permet d’afficher des contrôles de .NET Framework sur une boîte de dialogue modale ou non MFC.  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) et [qui héberge un contrôle Windows Form utilisateur comme une boîte de dialogue MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog  
 Construit un objet `CWinFormsDialog`.  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>Paramètres  
 `nIDTemplate`  
 Contient l’ID d’une ressource de modèle de boîte de dialogue. Utilisez l’éditeur de boîte de dialogue pour créer le modèle de boîte de dialogue et les stocker dans le fichier de script de ressources de l’application. Pour plus d’informations sur les modèles de boîte de dialogue, consultez [CDialog (classe)](../../mfc/reference/cdialog-class.md).  
  
##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl  
 Récupère une référence au contrôle utilisateur Windows Forms.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence au contrôle Windows Forms dans la boîte de dialogue MFC.  
  
##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle  
 Récupère un handle de fenêtre pour le contrôle utilisateur Windows Forms.  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un handle de fenêtre pour le contrôle utilisateur Windows Forms.  
  
##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog  
 Initialise la boîte de dialogue MFC par la création et l’hébergement d’un contrôle utilisateur Windows Forms.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur booléenne qui spécifie si l’application a défini le focus d’entrée à un des contrôles dans la boîte de dialogue. Si `OnInitDialog` retourne différente de zéro, Windows définit le focus d’entrée sur le premier contrôle dans la boîte de dialogue. Cette méthode peut retourner 0 uniquement si l’application a défini explicitement le focus d’entrée à un des contrôles dans la boîte de dialogue.  
  
### <a name="remarks"></a>Notes  
 Création de la boîte de dialogue MFC (à l’aide de la [créer](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), ou [DoModal](../../mfc/reference/cdialog-class.md#domodal) héritée de la méthode [CDialog](../../mfc/reference/cdialog-class.md)), un `WM_INITDIALOG` message est envoyé, cette méthode est appelée. Il crée une instance d’un contrôle Windows Forms dans la boîte de dialogue et ajuste la taille de la boîte de dialogue pour prendre en compte pour la taille du contrôle utilisateur. Puis il héberge le nouveau contrôle dans la boîte de dialogue MFC.  
  
 Remplacez cette fonction membre, si vous avez besoin effectuer un traitement spécial lors de l’initialisation de la boîte de dialogue. Pour plus d’informations sur l’utilisation de cette méthode, consultez [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).  
  
##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;  
 Remplace [CWinFormsDialog::GetControl](#getcontrol) dans les expressions.  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Cet opérateur fournit une syntaxe qui remplace `GetControl` dans les expressions.  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_tmanagedcontrol_xor"></a>  CWinFormsDialog::operator TManagedControl ^  
 Convertit un type en tant que référence à un contrôle utilisateur Windows Forms.  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Cet opérateur convertit un type en tant que référence à un contrôle Windows Forms. Il est utilisé pour passer un `CWinFormsDialog<TManagedControl>` boîte de dialogue pour les fonctions qui acceptent un pointeur vers un objet de contrôle utilisateur Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Classe CWinFormsView](../../mfc/reference/cwinformsview-class.md)   
 [CDialog, classe](../../mfc/reference/cdialog-class.md)
