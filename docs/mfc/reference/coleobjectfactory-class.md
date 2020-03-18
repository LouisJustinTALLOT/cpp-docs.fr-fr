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
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421540"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory (classe)

Implémente la fabrique de classes OLE, qui crée des objets OLE tels que des serveurs, des objets Automation et des documents.

## <a name="syntax"></a>Syntaxe

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[COleObjectFactory :: COleObjectFactory](#coleobjectfactory)|Construit un objet `COleObjectFactory`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[COleObjectFactory :: GetClassID](#getclassid)|Retourne l’ID de classe OLE des objets que cette fabrique crée.|
|[COleObjectFactory :: IsLicenseValid](#islicensevalid)|Détermine si la licence du contrôle est valide.|
|[COleObjectFactory :: IsRegistered](#isregistered)|Indique si la fabrique d’objets est inscrite auprès des DLL système OLE.|
|[COleObjectFactory :: Register](#register)|Inscrit cette fabrique d’objets avec les DLL système OLE.|
|[COleObjectFactory :: RegisterAll](#registerall)|Inscrit toutes les fabriques d’objets de l’application avec des DLL système OLE.|
|[COleObjectFactory :: Revoke](#revoke)|Révoque l’inscription de cette fabrique d’objets avec les DLL système OLE.|
|[COleObjectFactory :: RevokeAll](#revokeall)|Révoque les inscriptions des fabriques d’objets d’une application avec les DLL système OLE.|
|[COleObjectFactory :: UnregisterAll](#unregisterall)|Annule l’inscription de toutes les fabriques d’objets d’une application.|
|[COleObjectFactory :: UpdateRegistry](#updateregistry)|Inscrit cette fabrique d’objets auprès du Registre système OLE.|
|[COleObjectFactory :: UpdateRegistryAll](#updateregistryall)|Inscrit toutes les fabriques d’objets de l’application auprès du Registre système OLE.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[COleObjectFactory :: GetLicenseKey](#getlicensekey)|Demande une clé unique à partir de la DLL du contrôle.|
|[COleObjectFactory :: OnCreateObject](#oncreateobject)|Appelé par l’infrastructure pour créer un nouvel objet du type de cette fabrique.|
|[COleObjectFactory :: VerifyLicenseKey](#verifylicensekey)|Vérifie que la clé incorporée dans le contrôle correspond à la clé incorporée dans le conteneur.|
|[COleObjectFactory :: VerifyUserLicense](#verifyuserlicense)|Vérifie que le contrôle est concédé sous licence pour une utilisation au moment du Design.|

## <a name="remarks"></a>Notes

La classe `COleObjectFactory` possède des fonctions membres pour exécuter les fonctions suivantes :

- Gestion de l’inscription des objets.

- Mise à jour du Registre du système OLE, ainsi que de l’inscription au moment de l’exécution qui informe OLE que les objets sont en cours d’exécution et prêts à recevoir des messages.

- Application des licences en limitant l’utilisation du contrôle aux développeurs sous licence au moment de la conception et aux applications sous licence au moment de l’exécution.

- Enregistrement des fabriques d’objets de contrôle avec le registre système OLE.

Pour plus d’informations sur la création d’objets, consultez les articles [objets de données et sources de données (OLE)](../../mfc/data-objects-and-data-sources-ole.md) , [objets de données et sources de données : création et destruction](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Pour plus d’informations sur l’inscription, consultez l’article [inscription](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

##  <a name="coleobjectfactory"></a>COleObjectFactory :: COleObjectFactory

Construit un objet `COleObjectFactory`, l’initialise comme fabrique d’objets non inscrite et l’ajoute à la liste des fabriques.

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

*identificateur*<br/>
Référence à l’ID de classe OLE que cette fabrique d’objets représente.

*pRuntimeClass*<br/>
Pointeur vers la classe d’exécution des objets que C++ cette fabrique peut créer.

*bMultiInstance*<br/>
Indique si une seule instance de l’application peut prendre en charge plusieurs instanciations. Si la valeur est TRUE, plusieurs instances de l’application sont lancées pour chaque demande de création d’un objet.

*nFlags*<br/>
Contient un ou plusieurs des indicateurs suivants :

- `afxRegDefault` définit le modèle de thread sur ThreadingModel = Apartment.

- `afxRegInsertable` permet d’afficher le contrôle dans la boîte de dialogue **Insérer un objet** pour les objets OLE.

- `afxRegApartmentThreading` définit le modèle de thread dans le registre sur ThreadingModel = Apartment.

- `afxRegFreeThreading` définit le modèle de thread dans le registre sur ThreadingModel = Free.

   Vous pouvez combiner les deux indicateurs `afxRegApartmentThreading` et `afxRegFreeThreading` pour définir ThreadingModel = both. Pour plus d’informations sur l’inscription du modèle de thread, consultez [InprocServer32](/windows/win32/com/inprocserver32) dans le SDK Windows.

*lpszProgID*<br/>
Pointeur vers une chaîne contenant un identificateur de programme verbal, tel que « Microsoft Excel ».

### <a name="remarks"></a>Notes

Toutefois, pour utiliser l’objet, vous devez l’inscrire.

Pour plus d’informations, consultez [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="getclassid"></a>COleObjectFactory :: GetClassID

Retourne une référence à l’ID de classe OLE que cette fabrique représente.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à l’ID de classe OLE que cette fabrique représente.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="getlicensekey"></a>COleObjectFactory :: GetLicenseKey

Demande une clé de licence unique à partir de la DLL du contrôle et la stocke dans le BSTR désigné par *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé pour un usage futur.

*pbstrKey*<br/>
Pointeur vers un BSTR qui stocke la clé de licence.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la chaîne de la clé de licence n’est pas NULL ; Sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction retourne 0 et ne stocke rien dans le BSTR. Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit une substitution qui récupère la clé de licence du contrôle.

##  <a name="islicensevalid"></a>COleObjectFactory :: IsLicenseValid

Détermine si la licence du contrôle est valide.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Valeur de retour

TRUE si Successul ; Sinon, false.

##  <a name="isregistered"></a>COleObjectFactory :: IsRegistered

Retourne une valeur différente de zéro si la fabrique est inscrite auprès des DLL système OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fabrique est inscrite ; Sinon, 0.

##  <a name="oncreateobject"></a>COleObjectFactory :: OnCreateObject

Appelé par l’infrastructure pour créer un nouvel objet.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet créé. Elle peut lever une exception de mémoire en cas d’échec.

### <a name="remarks"></a>Notes

Substituez cette fonction pour créer l’objet à partir d’un autre nom que le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) passé au constructeur.

##  <a name="register"></a>COleObjectFactory :: Register

Inscrit cette fabrique d’objets avec les DLL système OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la fabrique est correctement inscrite ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp :: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

##  <a name="registerall"></a>COleObjectFactory :: RegisterAll

Inscrit toutes les fabriques d’objets de l’application avec les DLL système OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les fabriques sont inscrites avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp :: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

##  <a name="revoke"></a>COleObjectFactory :: Revoke

Révoque l’inscription de cette fabrique d’objets avec les DLL système OLE.

```
void Revoke();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction automatiquement avant que l’application ne se termine. Si nécessaire, appelez-le à partir d’une substitution de [CWinApp :: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>COleObjectFactory :: RevokeAll

Révoque toutes les inscriptions des fabriques d’objets de l’application avec les DLL système OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction automatiquement avant que l’application ne se termine. Si nécessaire, appelez-le à partir d’une substitution de [CWinApp :: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>COleObjectFactory :: UnregisterAll

Annule l’inscription de toutes les fabriques d’objets d’une application.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

##  <a name="updateregistry"></a>COleObjectFactory :: UpdateRegistry

Inscrit toutes les fabriques d’objets de l’application auprès du Registre système OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Paramètres

*lpszProgID*<br/>
Pointeur vers une chaîne contenant l’identificateur de programme lisible par l’utilisateur, tel que « Excel. document. 5 ».

*bRegister*<br/>
Détermine si la fabrique d’objet de la classe de contrôle doit être inscrite.

### <a name="remarks"></a>Notes

Voici quelques-unes des discussions sur les deux formes de cette fonction :

- **UpdateRegistry (** `lpszProgID` **)** Inscrit cette fabrique d’objets auprès du Registre système OLE. Cette fonction est généralement appelée par [CWinApp :: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

- **UpdateRegistry (** `bRegister` **)** Cette forme de la fonction est substituable. Si *bRegister* a la valeur true, cette fonction inscrit la classe de contrôle auprès du Registre système. Dans le cas contraire, il annule l’inscription de la classe.

   Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit un remplacement à cette fonction virtuelle pure.

##  <a name="updateregistryall"></a>COleObjectFactory :: UpdateRegistryAll

Inscrit toutes les fabriques d’objets de l’application auprès du Registre système OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Paramètres

*bRegister*<br/>
Détermine si la fabrique d’objet de la classe de contrôle doit être inscrite.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si les fabriques sont mises à jour avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp :: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

##  <a name="verifylicensekey"></a>COleObjectFactory :: VerifyLicenseKey

Vérifie que le conteneur est concédé sous licence pour utiliser le contrôle OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Paramètres

*bstrKey*<br/>
BSTR stockant la version du conteneur de la chaîne de licence.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la licence d’exécution est valide ; Sinon, 0.

### <a name="remarks"></a>Notes

La version par défaut appelle [GetLicenseKey](#getlicensekey) pour obtenir une copie de la chaîne de licence du contrôle et la compare à la chaîne dans *bstrKey*. Si les deux chaînes correspondent, la fonction retourne une valeur différente de zéro ; Sinon, elle retourne 0.

Vous pouvez remplacer cette fonction pour fournir une vérification personnalisée de la licence.

La fonction [VerifyUserLicense](#verifyuserlicense) vérifie la licence au moment du Design.

##  <a name="verifyuserlicense"></a>COleObjectFactory :: VerifyUserLicense

Vérifie la licence au moment du design pour le contrôle OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la licence au moment du design est valide ; Sinon, 0.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
