---
title: COleObjectFactory, classe
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
ms.openlocfilehash: 165ba7c1918c3ccc5d5d7e0bc067fba86678a3e7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753804"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory, classe

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
|[COleObjectFactory::GetClassID](#getclassid)|Retourne l’ID de classe OLE des objets que cette usine crée.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Détermine si la licence du contrôle est valide.|
|[COleObjectFactory::IsRegistered](#isregistered)|Indique si l’usine d’objets est enregistrée auprès des DLL du système OLE.|
|[COleObjectFactory::Enregistrement](#register)|Enregistre cette usine d’objets avec le système OLE DLLs.|
|[COleObjectFactory::RegisterAll](#registerall)|Enregistre toutes les usines d’objets de l’application avec le système OLE DLLs.|
|[COleObjectFactory::Revoke](#revoke)|Révoque l’enregistrement de cette usine d’objets auprès des DLL du système OLE.|
|[COleObjectFactory::RevokeAll](#revokeall)|Révoque les enregistrements d’usines d’objets d’une demande auprès des DLL du système OLE.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Désenregistrer toutes les usines d’objets d’une application.|
|[COleObjectFactory::Mise à jourRegistry](#updateregistry)|Enregistre cette usine d’objets avec le registre du système OLE.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Enregistre toutes les usines d’objets de l’application avec le registre du système OLE.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Demande une clé unique de la DLL du contrôle.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Appelé par le cadre pour créer un nouvel objet du type de cette usine.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Vérifie que la clé intégrée dans le contrôle correspond à la clé intégrée dans le conteneur.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Vérifie que le contrôle est autorisé pour l’utilisation de conception-temps.|

## <a name="remarks"></a>Notes

La `COleObjectFactory` classe a des fonctions de membre pour l’exécution des fonctions suivantes :

- Gestion de l’enregistrement des objets.

- Mise à jour du registre du système OLE, ainsi que l’enregistrement en temps d’exécution qui informe OLE que les objets sont en cours d’exécution et prêts à recevoir des messages.

- L’application des licences en limitant l’utilisation du contrôle aux développeurs sous licence au moment de la conception et aux demandes sous licence au moment de l’exécution.

- Enregistrement des usines d’objets de contrôle avec le registre du système OLE.

Pour plus d’informations sur la création d’objets, consultez les articles [Data Objects and Data Sources (OLE)](../../mfc/data-objects-and-data-sources-ole.md) et Data Objects and Data [Sources: Creation and Destruction](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Pour en savoir plus sur l’inscription, voir l’article [Inscription](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory

Construit un `COleObjectFactory` objet, l’initialise comme une usine d’objets non enregistrées, et l’ajoute à la liste des usines.

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
Référence à la classe OLE ID que représente cette usine d’objets.

*pRuntimeClass (en)*<br/>
Pointeur vers la classe de temps d’exécution des objets CMD que cette usine peut créer.

*bMultiInstance*<br/>
Indique si une seule instance de l’application peut prendre en charge plusieurs instantanés. Si VRAI, plusieurs instances de l’application sont lancées pour chaque demande de création d’un objet.

*nFlags*<br/>
Contient un ou plusieurs des drapeaux suivants :

- `afxRegDefault`Définit le modèle de threading à ThreadingModel-Apartment.

- `afxRegInsertable`Permet au contrôle d’apparaître dans la boîte de dialogue **Insert Object** pour les objets OLE.

- `afxRegApartmentThreading`Définit le modèle de threading dans le registre à ThreadingModel-Apartment.

- `afxRegFreeThreading`Définit le modèle de threading dans le registre à ThreadingModel-Free.

   Vous pouvez combiner `afxRegApartmentThreading` les `afxRegFreeThreading` deux drapeaux et définir ThreadingModel-Both. Voir [InprocServer32](/windows/win32/com/inprocserver32) dans le Windows SDK pour plus d’informations sur l’enregistrement des modèles de threading.

*lpszProgID*<br/>
Pointeur vers une chaîne contenant un identifiant de programme verbal, comme "Microsoft Excel".

### <a name="remarks"></a>Notes

Pour utiliser l’objet, cependant, vous devez l’enregistrer.

Pour plus d’informations, voir [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObjectFactory::GetClassID

Retourne une référence à l’ID de classe OLE que cette usine représente.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Valeur de retour

Référence à la classe OLE ID cette usine représente.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey

Demande une clé de licence unique de la DLL du contrôle et le stocke dans le BSTR pointé par *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
Réservé pour un usage futur.

*pbstrKey (en)*<br/>
Pointeur vers un BSTR qui stockera la clé de licence.

### <a name="return-value"></a>Valeur de retour

Nonzero si la chaîne de la clé de licence n’est pas NULL; sinon 0.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction retourne 0 et ne stocke rien dans le BSTR. Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit un remplacement qui récupère la clé de licence du contrôle.

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid

Détermine si la licence du contrôle est valide.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Valeur de retour

VRAI si successul; autrement faux.

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObjectFactory::IsRegistered

Retourne une valeur non zéro si l’usine est enregistrée auprès du système OLE DLLs.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’usine est enregistrée; sinon 0.

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObjectFactory::OnCreateObject

Appelé par le cadre pour créer un nouvel objet.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet créé. Il peut jeter une exception de mémoire si elle échoue.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour créer l’objet à partir de quelque chose d’autre que le [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) passé au constructeur.

## <a name="coleobjectfactoryregister"></a><a name="register"></a>COleObjectFactory::Enregistrement

Enregistre cette usine d’objets avec le système OLE DLLs.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’usine est enregistrée avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObjectFactory::RegisterAll

Enregistre toutes les usines d’objets de l’application avec le système OLE DLLs.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si les usines sont enregistrées avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObjectFactory::Revoke

Révoque l’enregistrement de cette usine d’objets auprès des DLL du système OLE.

```cpp
void Revoke();
```

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction automatiquement avant la fin de l’application. Si nécessaire, appelez-le à partir d’un remplacement de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObjectFactory::RevokeAll

Révoque toutes les inscriptions des usines d’objets de l’application auprès des DLL du système OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction automatiquement avant la fin de l’application. Si nécessaire, appelez-le à partir d’un remplacement de [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObjectFactory::UnregisterAll

Désenregistrer toutes les usines d’objets d’une application.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObjectFactory::Mise à jourRegistry

Enregistre toutes les usines d’objets de l’application avec le registre du système OLE.

```cpp
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Paramètres

*lpszProgID*<br/>
Pointeur vers une chaîne contenant l’identifiant de programme lisible par l’homme, comme « Excel.Document.5 ».

*bRegister (en)*<br/>
Détermine si l’usine d’objets de la classe de contrôle doit être enregistrée.

### <a name="remarks"></a>Notes

Voici de brèves discussions sur les deux formulaires pour cette fonction :

- **Mise à jourRegistry)** `lpszProgID` **)** Enregistre cette usine d’objets avec le registre du système OLE. Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

- **Mise à jourRegistry)** `bRegister` **)** Cette forme de la fonction est primordiale. Si *bRegister* est VRAI, cette fonction enregistre la classe de contrôle avec le registre du système. Sinon, il ne s’inscrit pas à la classe.

   Si vous utilisez MFC ActiveX ControlWizard pour créer votre projet, ControlWizard fournit un remplacement à cette fonction virtuelle pure.

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObjectFactory::UpdateRegistryAll

Enregistre toutes les usines d’objets de l’application avec le registre du système OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Paramètres

*bRegister (en)*<br/>
Détermine si l’usine d’objets de la classe de contrôle doit être enregistrée.

### <a name="return-value"></a>Valeur de retour

Nonzero si les usines sont mises à jour avec succès; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée par [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) lorsque l’application est lancée.

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey

Vérifie que le conteneur est autorisé à utiliser le contrôle OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Paramètres

*bstrKey (en)*<br/>
Un BSTR stockant la version du conteneur de la chaîne de licence.

### <a name="return-value"></a>Valeur de retour

Nonzero si la licence de temps d’exécution est valide; sinon 0.

### <a name="remarks"></a>Notes

La version par défaut appelle [GetLicenseKey](#getlicensekey) pour obtenir une copie de la chaîne de licence du contrôle et la compare avec la chaîne en *bstrKey*. Si les deux cordes correspondent, la fonction retourne une valeur non zéro; sinon il revient 0.

Vous pouvez remplacer cette fonction pour fournir une vérification personnalisée de la licence.

La fonction [VerifyUserLicense](#verifyuserlicense) vérifie la licence de conception-temps.

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense

Vérifie la licence de temps de conception pour le contrôle OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la licence de temps de conception est valide; sinon 0.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
