---
title: COleObjectFactory (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd68493c9be5eb0bff63504cf49b38b9a2f216d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375935"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory (classe)
Implémente la fabrique de classes OLE, qui crée des objets OLE tels que des serveurs, des objets Automation et des documents.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Construit un objet `COleObjectFactory`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|Retourne le OLE ID de classe de cette fabrique crée des objets.|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Détermine si la licence du contrôle est valide.|  
|[COleObjectFactory::IsRegistered](#isregistered)|Indique si la fabrique d’objet est inscrit avec les DLL système OLE.|  
|[COleObjectFactory::Register](#register)|Enregistre cette fabrique d’objet avec les DLL système OLE.|  
|[COleObjectFactory::RegisterAll](#registerall)|Enregistre tous les fabriques d’objet de l’application avec les DLL système OLE.|  
|[COleObjectFactory::Revoke](#revoke)|Révoque l’inscription de cette fabrique d’objet avec les DLL système OLE.|  
|[COleObjectFactory::RevokeAll](#revokeall)|Révoque les inscriptions des fabriques d’objets d’une application avec les DLL système OLE.|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|Annule l’inscription de toutes les fabriques d’objets d’une application.|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Enregistre cette fabrique d’objet avec le Registre du système OLE.|  
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Enregistre tous les fabriques d’objet de l’application avec le Registre du système OLE.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Demande une clé unique à partir de la DLL du contrôle.|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Appelé par l’infrastructure pour créer un nouvel objet de type de cette fabrique.|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Vérifie que la clé incorporée dans le contrôle correspond à la clé incorporée dans le conteneur.|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Vérifie que le contrôle est concédé sous licence pour les utiliser au moment du design.|  
  
## <a name="remarks"></a>Notes  
 La `COleObjectFactory` classe possède des fonctions de membre pour effectuer les fonctions suivantes :  
  
-   La gestion de l’inscription d’objets.  
  
-   Cette mise à jour le Registre du système OLE, ainsi que l’inscription de l’exécution qui informe OLE que les objets sont en cours d’exécution et prêt à recevoir des messages.  
  
-   L’application Gestionnaire de licences en limitant l’utilisation du contrôle aux développeurs sous licence au moment du design et des applications sous licence en cours d’exécution.  
  
-   L’inscription de fabriques d’objet de contrôle du Registre du système OLE.  
  
 Pour plus d’informations sur la création d’objets, consultez les articles [des objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md) et [des objets de données et Sources de données : création et Destruction](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Pour plus d’informations sur l’inscription, consultez l’article [inscription](../../mfc/registration.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory  
 Construit un `COleObjectFactory` objet, initialise comme une fabrique d’objet non et l’ajoute à la liste des fabriques.  
  
```  
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    LPCTSTR lpszProgID);

 
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    int nFlags,  
    LPCTSTR lpszProgID);
```  
  
### <a name="parameters"></a>Paramètres  
 `clsid`  
 Référence à l’ID de classe OLE cette fabrique d’objet représente.  
  
 `pRuntimeClass`  
 Pointeur vers la classe d’exécution des objets C++ que cette fabrique peut créer.  
  
 `bMultiInstance`  
 Indique si une seule instance de l’application peut prendre en charge plusieurs instanciations. Si **TRUE**, plusieurs instances de l’application sont lancées pour chaque demande de création d’un objet.  
  
 `nFlags`  
 Contient un ou plusieurs des indicateurs suivants :  
  
- **afxRegDefault** définit le modèle de thread à ThreadingModel = cloisonnement.  
  
- **afxRegInsertable** permet le contrôle s’affiche dans le **insérer un objet** boîte de dialogue pour les objets OLE.  
  
- `afxRegApartmentThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = cloisonnement.  
  
- **afxRegFreeThreading** définit le modèle de thread dans le Registre pour ThreadingModel = libre.  
  
     Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` pour définir ThreadingModel = les deux. Consultez [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) dans le SDK Windows pour plus d’informations sur l’inscription du modèle de thread.  
  
 `lpszProgID`  
 Pointeur vers une chaîne contenant un identificateur de programme verbaux, telle que « Microsoft Excel ».  
  
### <a name="remarks"></a>Notes  
 Pour utiliser l’objet, toutefois, vous devez l’inscrire.  
  
 Pour plus d’informations, consultez [clé CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) dans le Kit de développement logiciel Windows.  
  
##  <a name="getclassid"></a>  COleObjectFactory::GetClassID  
 Retourne une référence à l’ID de classe OLE représente de cette fabrique.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à l’ID de classe OLE cette fabrique représente.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [clé CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) dans le Kit de développement logiciel Windows.  
  
##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey  
 Demande une clé de licence unique à partir de la DLL du contrôle et le stocke dans le `BSTR` vers lequel pointe `pbstrKey`.  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwReserved`  
 Réservé à un usage ultérieur.  
  
 `pbstrKey`  
 Pointeur vers un `BSTR` qui stocke la clé de licence.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la chaîne de clé de licence n’est pas **NULL**; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut de cette fonction retourne 0 et stocke rien dans le `BSTR`. Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit un remplacement qui Récupère la clé de licence du contrôle.  
  
##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid  
 Détermine si la licence du contrôle est valide.  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la réussite ; Sinon, false.  
  
##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered  
 Retourne une valeur différente de zéro si la fabrique est enregistrée avec les DLL système OLE.  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fabrique est inscrit ; Sinon, 0.  
  
##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject  
 Appelé par l’infrastructure pour créer un nouvel objet.  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’objet créé. Il peut lever une exception de mémoire en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Remplacez cette fonction pour créer l’objet d’un élément autre que le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) passé au constructeur.  
  
##  <a name="register"></a>  COleObjectFactory::Register  
 Enregistre cette fabrique d’objet avec les DLL système OLE.  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la fabrique est enregistrée avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.  
  
##  <a name="registerall"></a>  COleObjectFactory::RegisterAll  
 Enregistre tous les fabriques d’objet de l’application avec les DLL système OLE.  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les fabriques sont enregistrés avec succès ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.  
  
##  <a name="revoke"></a>  COleObjectFactory::Revoke  
 Révoque l’inscription de cette fabrique d’objet avec les DLL système OLE.  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction automatiquement avant l’arrêt de l’application. Si nécessaire, l’appeler à partir d’une substitution de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll  
 Révoque tous les enregistrements des fabriques d’objets de l’application avec les DLL système OLE.  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>Notes  
 L’infrastructure appelle cette fonction automatiquement avant l’arrêt de l’application. Si nécessaire, l’appeler à partir d’une substitution de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll  
 Annule l’inscription de toutes les fabriques d’objets d’une application.  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE en cas de réussite, sinon FALSE.  
  
##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry  
 Enregistre tous les fabriques d’objet de l’application avec le Registre du système OLE.  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszProgID`  
 Pointeur vers une chaîne contenant l’identificateur de programme explicite, comme « Excel.Document.5 ».  
  
 `bRegister`  
 Détermine si la fabrique d’objet de la classe du contrôle doit être enregistré.  
  
### <a name="remarks"></a>Notes  
 Procédez de la brèves discussions de deux formulaires pour cette fonction :  
  
- **UpdateRegistry (** `lpszProgID` **)** enregistre cette fabrique d’objet du Registre du système OLE. Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.  
  
- **UpdateRegistry (** `bRegister` **)** cette forme de la fonction est substituable. Si `bRegister` est **TRUE**, cette fonction enregistre la classe de contrôle du Registre système. Dans le cas contraire, il annule l’inscription de la classe.  
  
     Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit une substitution de cette fonction virtuelle pure.  
  
##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll  
 Enregistre tous les fabriques d’objet de l’application avec le Registre du système OLE.  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `bRegister`  
 Détermine si la fabrique d’objet de la classe du contrôle doit être enregistré.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si les fabriques sont correctement mis à jour ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.  
  
##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey  
 Vérifie que le conteneur est concédé sous licence pour utiliser le contrôle OLE.  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrKey`  
 A `BSTR` le stockage de la version du conteneur de la chaîne de licence.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la licence d’exécution n’est valide. Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 La version par défaut appelle [GetLicenseKey](#getlicensekey) pour obtenir une copie du contrôle de la chaîne de licence et la compare à la chaîne dans `bstrKey`. Si les deux chaînes sont identiques, la fonction retourne une valeur différente de zéro ; Sinon, elle retourne 0.  
  
 Vous pouvez substituer cette fonction pour fournir une vérification personnalisée de la licence.  
  
 La fonction [VerifyUserLicense](#verifyuserlicense) vérifie la licence au moment du design.  
  
##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense  
 Vérifie la licence au moment du design pour le contrôle OLE.  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la licence au moment du design n’est valide. Sinon, 0.  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
