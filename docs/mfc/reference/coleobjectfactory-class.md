---
title: COleObjectFactory (classe)
ms.date: 11/04/2016
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
ms.openlocfilehash: 4aa6d688de59884c7279b441d12dda9dcdf2ff6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476009"
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
|[COleObjectFactory::GetClassID](#getclassid)|Retourne le OLE ID de classe des objets que cette fabrique crée.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Détermine si la licence du contrôle est valide.|
|[COleObjectFactory::IsRegistered](#isregistered)|Indique si la fabrique d’objet est inscrit avec les DLL système OLE.|
|[COleObjectFactory](#register)|Inscrit cette fabrique d’objet avec les DLL système OLE.|
|[COleObjectFactory::RegisterAll](#registerall)|Enregistre toutes les fabriques d’objets de l’application avec les DLL système OLE.|
|[COleObjectFactory::Revoke](#revoke)|Révoque l’inscription de cette fabrique d’objet avec les DLL système OLE.|
|[COleObjectFactory::RevokeAll](#revokeall)|Révoque les enregistrements des fabriques d’objet d’une application avec les DLL système OLE.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Annule l’inscription de toutes les fabriques d’objet d’une application.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Inscrit cette fabrique d’objet avec le Registre du système OLE.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Enregistre toutes les fabriques d’objet de l’application avec le Registre du système OLE.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Demande une clé unique à partir de la DLL du contrôle.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Appelé par le framework pour créer un nouvel objet de type de cette fabrique.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Vérifie que la clé incorporée dans le contrôle correspond à la clé incorporée dans le conteneur.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Vérifie que le contrôle est concédée sous licence au moment du design.|

## <a name="remarks"></a>Notes

Le `COleObjectFactory` classe possède des fonctions de membre pour effectuer les fonctions suivantes :

- La gestion de l’inscription d’objets.

- La mise à jour le Registre du système OLE, ainsi que l’inscription de l’exécution qui informe OLE que les objets sont en cours d’exécution et prêt à recevoir des messages.

- L’application de gestion des licences en limitant l’utilisation du contrôle aux développeurs sous licence au moment du design et des applications sous licence en cours d’exécution.

- L’inscription de fabriques d’objet de contrôle du Registre du système OLE.

Pour plus d’informations sur la création d’objets, consultez les articles [objets de données et Sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md) et [objets de données et Sources de données : création et la Destruction](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Pour plus d’informations sur l’inscription, consultez l’article [inscription](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory

Construit un `COleObjectFactory` objet, il initialise comme une fabrique d’objet non inscrit et l’ajoute à la liste des fabriques de.

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

*clsid*<br/>
Référence à l’ID de classe OLE cette fabrique d’objet représente.

*pRuntimeClass*<br/>
Pointeur vers la classe d’exécution des objets C++ que cette fabrique peut créer.

*bMultiInstance*<br/>
Indique si une seule instance de l’application peut prendre en charge de plusieurs instanciations. Si la valeur est TRUE, plusieurs instances de l’application sont lancées pour chaque demande de création d’un objet.

*nIndicateurs*<br/>
Contient un ou plusieurs des indicateurs suivants :

- `afxRegDefault` Définit le modèle de thread à ThreadingModel = apartment (cloisonné).

- `afxRegInsertable` Permet le contrôle s’affiche dans le **insérer un objet** boîte de dialogue pour les objets OLE.

- `afxRegApartmentThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = apartment (cloisonné).

- `afxRegFreeThreading` Définit le modèle de thread dans le Registre pour ThreadingModel = gratuit.

   Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` pour définir ThreadingModel = Both. Consultez [InprocServer32](/windows/desktop/com/inprocserver32) dans le SDK Windows pour plus d’informations sur l’inscription du modèle de thread.

*lpszProgID*<br/>
Pointeur vers une chaîne contenant un identificateur de programme verbale, telles que « Microsoft Excel ».

### <a name="remarks"></a>Notes

Pour utiliser l’objet, toutefois, vous devez l’inscrire.

Pour plus d’informations, consultez [clé CLSID](/windows/desktop/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="getclassid"></a>  COleObjectFactory::GetClassID

Retourne une référence à l’ID de classe OLE représente cette fabrique.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à l’ID de classe OLE cette fabrique représente.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [clé CLSID](/windows/desktop/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey

Demande une clé de licence unique à partir de la DLL du contrôle et le stocke dans le BSTR vers lequel pointé *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé à un usage ultérieur.

*pbstrKey*<br/>
Pointeur vers un BSTR qui stocke la clé de licence.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la chaîne de clé de licence n’est pas NULL ; sinon 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction retourne 0 et ne stocke rien dans le BSTR. Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit un remplacement qui Récupère la clé de licence du contrôle.

##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid

Détermine si la licence du contrôle est valide.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Valeur de retour

TRUE si réussite ; Sinon, false.

##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered

Retourne une valeur différente de zéro si la fabrique est enregistrée avec les DLL système OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fabrique est inscrit ; sinon 0.

##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject

Appelé par le framework pour créer un nouvel objet.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet créé. Il peut lever une exception de mémoire en cas d’échec.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour créer l’objet d’un élément autre que le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) passé au constructeur.

##  <a name="register"></a>  COleObjectFactory

Inscrit cette fabrique d’objet avec les DLL système OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fabrique est inscrit avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

##  <a name="registerall"></a>  COleObjectFactory::RegisterAll

Enregistre toutes les fabriques d’objet de l’application avec les DLL système OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les fabriques sont inscrites avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

##  <a name="revoke"></a>  COleObjectFactory::Revoke

Révoque l’inscription de cette fabrique d’objet avec les DLL système OLE.

```
void Revoke();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction automatiquement avant l’application se termine. Si nécessaire, appelez-la à partir d’une substitution de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll

Révoque tous les enregistrements des fabriques d’objet de l’application avec les DLL système OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction automatiquement avant l’application se termine. Si nécessaire, appelez-la à partir d’une substitution de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll

Annule l’inscription de toutes les fabriques d’objet d’une application.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry

Enregistre toutes les fabriques d’objet de l’application avec le Registre du système OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Paramètres

*lpszProgID*<br/>
Pointeur vers une chaîne contenant l’identificateur de programme explicite, comme « Excel.Document.5 ».

*bRegister*<br/>
Détermine si la fabrique d’objet de la classe de contrôle doit être enregistré.

### <a name="remarks"></a>Notes

Brève discussions des deux formes pour cette fonction de suivi :

- **UpdateRegistry (** `lpszProgID` **)** inscrit cette fabrique d’objet avec le Registre du système OLE. Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

- **UpdateRegistry (** `bRegister` **)** cette forme de la fonction est substituable. Si *bRegister* a la valeur TRUE, cette fonction enregistre le contrôle de classe avec le Registre système. Sinon, il annule l’inscription de la classe.

   Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit un remplacement pour cette fonction virtuelle pure.

##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll

Enregistre toutes les fabriques d’objet de l’application avec le Registre du système OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Paramètres

*bRegister*<br/>
Détermine si la fabrique d’objet de la classe de contrôle doit être enregistré.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les fabriques sont correctement mis à jour ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey

Vérifie que le conteneur est concédé sous licence pour utiliser le contrôle OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Paramètres

*bstrKey*<br/>
BSTR stocker la version du conteneur de la chaîne de licence.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la licence de l’exécution est valide ; sinon 0.

### <a name="remarks"></a>Notes

La version par défaut appelle [GetLicenseKey](#getlicensekey) pour obtenir une copie du contrôle de la chaîne de licence et la compare à la chaîne dans *bstrKey*. Si les deux chaînes correspondent, la fonction retourne une valeur différente de zéro ; Sinon, elle retourne 0.

Vous pouvez remplacer cette fonction pour assurer une vérification personnalisée de la licence.

La fonction [VerifyUserLicense](#verifyuserlicense) vérifie la licence au moment du design.

##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense

Vérifie la licence au moment du design pour le contrôle OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la licence au moment du design est valide ; sinon 0.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
