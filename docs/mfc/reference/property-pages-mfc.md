---
title: Pages de propriétés (MFC) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3c3270f76c6231a669bcf848680793cc924391b
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338988"
---
# <a name="property-pages-mfc"></a>Pages de propriétés (MFC)
Pages de propriétés affichent les valeurs actuelles des propriétés de contrôle OLE spécifiques dans une interface graphique personnalisable pour afficher et modifier en prenant en charge un mécanisme de mappage de données basé sur l’échange de données de boîtes de dialogue (DDX).  
  
 Ce mécanisme de mappage de données mappe les contrôles de page de propriété pour les propriétés individuelles du contrôle OLE. La valeur de la propriété du contrôle reflète l’état ou le contenu du contrôle de page de propriété. Le mappage entre propriétés et les contrôles de page de propriété spécifié par **DDP_** appels de fonction dans la page de propriétés `DoDataExchange` fonction membre. Voici une liste de **DDP_** fonctions qui échangent des données entrées à l’aide de la page de propriétés de votre contrôle :  
  
### <a name="property-page-data-transfer"></a>Transfert de données de la Page de propriété  
  
|||  
|-|-|  
|[DDP_CBIndex](#ddp_cbindex)|Lie les index de la chaîne sélectionnée dans une zone de liste déroulante avec la propriété d’un contrôle.|  
|[DDP_CBString](#ddp_cbstring)|Lie la chaîne sélectionnée dans une zone de liste déroulante avec la propriété d’un contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de propriété, mais pas nécessairement correspondre totalement.|  
|[DDP_CBStringExact](#ddp_cbstringexact)|Lie la chaîne sélectionnée dans une zone de liste déroulante avec la propriété d’un contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|  
|[DDP_Check](#ddp_check)|Lie une case à cocher dans la page de propriétés du contrôle avec la propriété d’un contrôle.|  
|[DDP_LBIndex](#ddp_lbindex)|Lie les index de la chaîne sélectionnée dans une zone de liste avec la propriété d’un contrôle.|  
|[DDP_LBString](#ddp_lbstring)|Lie la chaîne sélectionnée dans une zone de liste avec la propriété d’un contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de propriété, mais n’est pas forcément il entièrement.|  
|[DDP_LBStringExact](#ddp_lbstringexact)|Lie la chaîne sélectionnée dans une zone de liste avec la propriété d’un contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|  
|[DDP_PostProcessing](#ddp_postprocessing)|Termine le transfert des valeurs de propriété à partir de votre contrôle.|  
|[DDP_Radio](#ddp_radio)|Un groupe de cases d’option dans la page de propriétés du contrôle avec la propriété d’un contrôle de liens.|  
|[DDP_TEXT](#ddp_text)|Lie un contrôle dans la page de propriétés du contrôle avec la propriété d’un contrôle. Cette fonction gère les différents types de propriétés, telles que **double**, **court**, BSTR, et **long**.|  
  
 Pour plus d’informations sur la `DoDataExchange` pages de fonction et une propriété, consultez l’article [contrôles ActiveX : Pages de propriétés](../../mfc/mfc-activex-controls-property-pages.md).  
  
 Voici une liste de macros permettant de créer et gérer des pages de propriétés d’un contrôle OLE :  
  
### <a name="property-pages"></a>Pages de propriétés  
  
|||  
|-|-|  
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Commence la liste des ID de page de propriété.|  
|[END_PROPPAGEIDS](#end_proppageids)|Met fin à la liste des ID de page de propriété.|  
|[PROPPAGEID](#proppageid)|Déclare une page de propriétés de la classe de contrôle.|  
  
##  <a name="ddp_cbindex"></a>  DDP_CBIndex  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction) pour synchroniser la valeur d’une propriété d’entier avec l’index de la sélection actuelle dans une zone de liste déroulante sur la page de propriétés.  
  
```   
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource de la liste déroulante zone de contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec le contrôle de zone de liste déroulante spécifié par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_CBIndex` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_cbstring"></a>  DDP_CBString  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction) pour synchroniser la valeur de propriété de type chaîne avec la sélection actuelle dans une zone de liste déroulante sur la page de propriétés.  
  
```  
void AFXAPI DDP_CBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource de la liste déroulante zone de contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec la chaîne de zone de liste déroulante spécifiée par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_CBString` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_cbstringexact"></a>  DDP_CBStringExact  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction) pour synchroniser la valeur d’une propriété de chaîne qui correspond exactement à la sélection actuelle dans une zone de liste déroulante sur la page de propriétés.  
  
```  
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource de la liste déroulante zone de contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec la chaîne de zone de liste déroulante spécifiée par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_CBStringExact` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_check"></a>  DDP_Check  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction) pour synchroniser la valeur de la propriété avec le contrôle de case à cocher de page de propriété associée.  
  
```   
void AFXAPI DDP_Check(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource du contrôle de case à cocher associée à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec le contrôle de case à cocher spécifié par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_Check` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_lbindex"></a>  DDP_LBIndex  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction) pour synchroniser la valeur d’une propriété d’entier avec l’index de la sélection actuelle dans une zone de liste sur la page de propriétés.  
  
```   
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,  
    int id,  
    int& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource de la liste de zone de contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec la chaîne de zone de liste spécifiée par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_LBIndex` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_lbstring"></a>  DDP_LBString  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction) pour synchroniser la valeur de propriété de type chaîne avec la sélection actuelle dans une zone de liste sur la page de propriétés.  
  
```   
void AFXAPI DDP_LBString(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource de la liste de zone de contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec la chaîne de zone de liste spécifiée par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_LBString` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_lbstringexact"></a>  DDP_LBStringExact  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction) pour synchroniser la valeur d’une propriété de chaîne qui correspond exactement à la sélection actuelle dans une zone de liste sur la page de propriétés.  
  
```   
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,  
    int id,  
    CString& member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource de la liste de zone de contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec la chaîne de zone de liste spécifiée par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_LBStringExact` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_postprocessing"></a>  DDP_PostProcessing  
 Appelez cette fonction dans votre page de propriétés `DoDataExchange` (fonction), pour terminer le transfert des valeurs de propriété à partir de la page de propriétés à votre contrôle lors de l’enregistrement des valeurs de propriété.  
  
```   
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée une fois que toutes les fonctions d’échange de données sont terminées. Exemple :  
  
 [!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_radio"></a>  DDP_Radio  
 Appelez cette fonction dans de votre contrôle `DoPropExchange` (fonction) pour synchroniser la valeur de la propriété du contrôle de bouton de case d’option de page propriété associée.  
  
```   
void AFXAPI DDP_Radio(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource de la case d’option bouton contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec le contrôle de bouton radio spécifié par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_Radio` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="ddp_text"></a>  DDP_TEXT  
 Appelez cette fonction dans de votre contrôle `DoDataExchange` (fonction) pour synchroniser la valeur de la propriété avec le contrôle de page de propriété associée.  
  
```   
void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    BYTE & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    int & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    UINT & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    long & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    DWORD & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    float & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    double & member,  
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,  
    int id,  
    CString & member,  
    LPCTSTR pszPropName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pDX*  
 Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.  
  
 *ID*  
 L’ID de ressource du contrôle associé à la propriété du contrôle spécifiée par *pszPropName*.  
  
 *Membre*  
 La variable de membre associée au contrôle de page de propriété spécifié par *id* et la propriété spécifiée par *pszPropName*.  
  
 *pszPropName*  
 Le nom de propriété de la propriété de contrôle à être échangés avec le contrôle spécifié par *id*.  
  
### <a name="remarks"></a>Notes  
 Cette fonction doit être appelée avant le correspondantes `DDX_Text` appel de fonction.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="begin_proppageids"></a>  BEGIN_PROPPAGEIDS  
 Commence la définition de liste de votre contrôle de l’ID de page de propriété.  
  
```   
BEGIN_PROPPAGEIDS(class_name,  count)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe de contrôle pour la propriété pages sont spécifiés.  
  
 *count*  
 Le nombre de pages de propriétés utilisées par la classe de contrôle.  
  
### <a name="remarks"></a>Notes  
 Dans le fichier d’implémentation (.cpp) qui définit les fonctions membres pour votre classe, démarrez la liste de page de propriétés avec la macro BEGIN_PROPPAGEIDS, puis ajouter des entrées de macro pour chacune de vos pages de propriété et compléter la liste de page de propriété avec le END_PROPPAGEIDS macro.  
  
 Pour plus d’informations sur les pages de propriétés, consultez l’article [contrôles ActiveX : Pages de propriétés](../../mfc/mfc-activex-controls-property-pages.md).  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="end_proppageids"></a>  END_PROPPAGEIDS  
 Met fin à la définition de votre liste de ID de page de propriétés.  
  
```   
END_PROPPAGEIDS(class_name)   
```  
  
### <a name="parameters"></a>Paramètres  
 *CLASS_NAME*  
 Le nom de la classe de contrôle qui possède la page de propriétés.  
  
### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
  
##  <a name="proppageid"></a>  PROPPAGEID  
 Ajoute une page de propriétés pour une utilisation par votre contrôle OLE.  
  
```   
PROPPAGEID(clsid)   
```  
  
### <a name="parameters"></a>Paramètres  
 *clsid*  
 L’ID de classe unique d’une page de propriétés.  
  
### <a name="remarks"></a>Notes  
 Toutes les macros PROPPAGEID doivent être placés entre les macros BEGIN_PROPPAGEIDS et END_PROPPAGEIDS dans le fichier d’implémentation de votre contrôle.  

### <a name="requirements"></a>Configuration requise  
  **En-tête** afxctl.h  
    
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
