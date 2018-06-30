---
title: Classe de CUserTool | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
dev_langs:
- C++
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 925e93afae4682497263eb96832aa466c6034231
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121314"
---
# <a name="cusertool-class"></a>Classe de CUserTool
Un outil utilisateur est un élément de menu qui exécute une application externe. Le **outils** onglet de la **personnaliser** boîte de dialogue ( [CMFCToolBarsCustomizeDialog classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) permet à l’utilisateur d’ajouter des outils de l’utilisateur et pour spécifier le nom, les commandes, les arguments, et répertoire initial de chaque outil utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CUserTool : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||  
|[CUserTool::DrawToolIcon](#drawtoolicon)|Dessine l’icône d’outil de l’utilisateur dans un rectangle spécifié.|  
|[CUserTool::GetCommand](#getcommand)|Retourne une chaîne qui contienne le texte de la commande associée à l’outil utilisateur.|  
|[CUserTool::GetCommandId](#getcommandid)|Retourne l’ID de commande de l’élément de menu de l’outil.|  
|[CUserTool::Invoke](#invoke)|Exécute la commande associée à l’outil utilisateur.|  
|[CUserTool::Serialize](#serialize)|Lit ou écrit cet objet dans une archive. (Substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CUserTool::SetCommand](#setcommand)|Définit la commande associée à l’outil utilisateur.|  
|[CUserTool::SetToolIcon](#settoolicon)|Charge l’icône de l’outil de l’utilisateur à partir de l’application associée à l’outil.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Charge l’icône par défaut pour un outil utilisateur.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CUserTool::m_strArguments](#m_strarguments)|Les arguments de ligne de commande pour l’outil utilisateur.|  
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Le répertoire initial de l’outil utilisateur.|  
|[CUserTool::m_strLabel](#m_strlabel)|Nom de l’outil qui s’affiche dans l’élément de menu de l’outil.|  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur la façon d’activer les outils utilisateur dans votre application, consultez [CUserToolsManager classe](../../mfc/reference/cusertoolsmanager-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un outil à partir d’un `CUserToolsManager` de l’objet, définissez la `m_strLabel` variable membre et ensemble de l’application qui exécute l’outil de l’utilisateur. Cet extrait de code fait partie de la [exemple de démonstration Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CUserTool](../../mfc/reference/cusertool-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxusertool.h  
  
##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CopyIconToClipboard();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon  
 Dessine l’icône d’outil de l’utilisateur dans le centre d’un rectangle spécifié.  
  
```  
void DrawToolIcon(
    CDC* pDC,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique.  
  
 [in] *rectImage*  
 Spécifie les coordonnées de la zone pour afficher l’icône.  
  
##  <a name="getcommand"></a>  CUserTool::GetCommand  
 Retourne une chaîne qui contienne le texte de la commande associée à l’outil utilisateur.  
  
```  
const CString& GetCommand() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une référence à `CString` objet qui contienne le texte de la commande associée à l’outil utilisateur.  
  
##  <a name="getcommandid"></a>  CUserTool::GetCommandId  
 Retourne l’ID de commande de l’outil.  
  
```  
UINT GetCommandId() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’ID de commande de cet outil utilisateur.  
  
##  <a name="invoke"></a>  CUserTool::Invoke  
 Exécute la commande associée à l’outil utilisateur.  
  
```  
virtual BOOL Invoke();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la commande a été exécutée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Appels [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) pour exécuter une commande associée à l’outil utilisateur. La fonction échoue si la commande est vide ou si [ShellExecute](http://msdn.microsoft.com/library/windows/desktop/bb762153) échoue.  
  
##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon  
 Charge l’icône par défaut pour un outil utilisateur.  
  
```  
virtual HICON LoadDefaultIcon();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers l’icône chargé (HICON), ou NULL si l’icône par défaut ne peut pas être chargé.  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette méthode lorsqu’il est impossible de charger une icône pour un outil défini par l’utilisateur à partir du fichier exécutable de l’outil.  
  
 Substituez cette méthode pour fournir votre propre icône par défaut de l’outil.  
  
##  <a name="m_strarguments"></a>  CUserTool::m_strArguments  
 Les arguments de ligne de commande pour l’outil utilisateur.  
  
```  
CString m_strArguments;  
```  
  
### <a name="remarks"></a>Notes  
 Cette chaîne est passée à l’outil lorsque vous appelez [CUserTool::Invoke](#invoke) ou lorsqu’un utilisateur clique sur la commande associée à cet outil.  
  
##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory  
 Spécifie le répertoire initial de l’outil utilisateur.  
  
```  
CString m_strInitialDirectory;  
```  
  
### <a name="remarks"></a>Notes  
 Cette variable Spécifie le répertoire initial de l’outil s’exécute dans lorsque vous appelez [CUserTool::Invoke](#invoke) ou lorsqu’un utilisateur clique sur la commande associée à cet outil.  
  
##  <a name="m_strlabel"></a>  CUserTool::m_strLabel  
 L’étiquette qui s’affiche dans l’élément de menu de l’outil.  
  
```  
CString m_strLabel;  
```  
  
##  <a name="serialize"></a>  CUserTool::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *ar*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setcommand"></a>  CUserTool::SetCommand  
 Définit l’application qui exécute l’outil de l’utilisateur.  
  
```  
void SetCommand(LPCTSTR lpszCmd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszCmd*  
 Spécifie la nouvelle application à associer à l’outil utilisateur.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour définir une nouvelle application qui exécute l’outil de l’utilisateur. La méthode détruit l’icône ancien et charge une nouvelle icône de l’application donnée. Si elle ne peut pas charger une icône de l’application, il charge l’icône par défaut pour un outil utilisateur en appelant [CUserTool::LoadDefaultIcon](#loaddefaulticon).  
  
##  <a name="settoolicon"></a>  CUserTool::SetToolIcon  
 Charge l’icône de l’outil de l’utilisateur à partir de l’application qui utilise de l’outil.  
  
```  
virtual HICON SetToolIcon();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Handle vers l’icône chargé.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour charger l’icône à afficher sur l’élément de menu. Cette méthode de recherche de l’icône dans le fichier exécutable que l’outil utilise. Si elle n’a pas d’une icône par défaut, l’icône fournie par [CUserTool::LoadDefaultIcon](#loaddefaulticon) est utilisé à la place.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [CUserToolsManager, classe](../../mfc/reference/cusertoolsmanager-class.md)
