---
title: COleLinkingDoc, classe
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: 275119b2343c4d13b6a32f939fc8c3b2b5d5890c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300403"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc, classe

Classe de base des documents de conteneur OLE qui prennent en charge la liaison aux éléments incorporés qu'ils contiennent.

## <a name="syntax"></a>Syntaxe

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Construit un objet `COleLinkingDoc`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleLinkingDoc::Register](#register)|Enregistre le document avec les DLL système OLE.|
|[COleLinkingDoc::Revoke](#revoke)|Révoque l’inscription du document.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Recherche l’élément incorporé spécifié.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Recherche l’élément lié spécifié.|

## <a name="remarks"></a>Notes

Une application de conteneur qui prend en charge la liaison à des éléments incorporés est appelée « conteneur de liaison ». Le [OCLIENT](../../visual-cpp-samples.md) exemple d’application est un exemple d’un conteneur de lien.

Lorsque la source de l’un élément lié est un élément incorporé dans un autre document, que contenant le document doit être chargé pour l’élément incorporé à modifier. Pour cette raison, un conteneur de lien doit pouvoir être lancé par une autre application de conteneur lorsque l’utilisateur souhaite modifier la source d’un élément lié. Votre application doit également utiliser le [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) classe afin qu’elle peut créer des documents lorsqu’elle est lancée par programmation.

Pour rendre votre conteneur à un conteneur de lien, dérivez votre classe de document de `COleLinkingDoc` au lieu de [COleDocument](../../mfc/reference/coledocument-class.md). Comme avec tout autre conteneur OLE, vous devez concevoir votre classe pour le stockage de l’application natives données ainsi que des éléments liés ou incorporés. En outre, vous devez concevoir des structures de données pour le stockage des données natives. Si vous définissez un `CDocItem`-classe dérivée de votre application native pour les données, vous pouvez utiliser l’interface définie par `COleDocument` pour stocker vos données natives, ainsi que vos données d’OLE.

Pour autoriser votre application doit être lancée par programme par un autre conteneur, déclarez un `COleTemplateServer` objet en tant que membre de votre application `CWinApp`-classe dérivée :

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

Dans le `InitInstance` fonction membre de votre `CWinApp`-classe dérivée, créez un modèle de document et spécifiez votre `COleLinkingDoc`-classe comme classe de document dérivée :

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Connecter votre `COleTemplateServer` objet à vos modèles de document en appelant l’objet `ConnectTemplate` fonction membre et inscrire une classe tous les objets avec le système OLE en appelant `COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Pour obtenir un exemple `CWinApp`-dérivée de définition de classe et `InitInstance` de fonction, consultez OCLIENT. H et OCLIENT. CPP dans l’exemple MFC [OCLIENT](../../visual-cpp-samples.md).

Pour plus d’informations sur l’utilisation de `COleLinkingDoc`, consultez les articles [conteneurs : Implémentation d’un conteneur](../../mfc/containers-implementing-a-container.md) et [conteneurs : Fonctionnalités avancées](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Spécifications

**En-tête :** afxole.h

##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc

Construit un `COleLinkingDoc` objet sans depuis les communications avec les DLL système OLE.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Notes

Vous devez appeler la `Register` fonction membre pour informer OLE que le document est ouvert.

##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem

Appelé par l’infrastructure pour déterminer si le document contient un élément OLE incorporé avec le nom spécifié.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName*<br/>
Pointeur vers le nom de l’OLE incorporé élément demandé.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’élément spécifié ; NULL si l’élément est introuvable.

### <a name="remarks"></a>Notes

L’implémentation par défaut recherche dans la liste des éléments incorporés pour un élément portant le nom spécifié (la comparaison de nom respecte la casse). Remplacez cette fonction si vous avez vos propres méthodes de stockage ou d’affectation de noms des éléments OLE incorporés.

##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem

Appelé par l’infrastructure pour vérifier si le document contient un élément de serveur lié avec le nom spécifié.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName*<br/>
Pointeur vers le nom de l’élément demandé de OLE lié.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’élément spécifié ; NULL si l’élément est introuvable.

### <a name="remarks"></a>Notes

La valeur par défaut `COleLinkingDoc` implémentation retourne toujours NULL. Cette fonction est substituée dans la classe dérivée `COleServerDoc` pour rechercher la liste des éléments de serveur OLE pour un élément lié portant le nom spécifié (la comparaison de nom respecte la casse). Remplacez cette fonction si vous avez implémenté votre propre méthode de stockage ou l’extraction d’éléments de serveur lié.

##  <a name="register"></a>  COleLinkingDoc::Register

Informe les DLL système OLE que le document est ouvert.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Paramètres

*pFactory*<br/>
Pointeur vers un objet de fabrique OLE (peut être pas NULL).

*lpszPathName*<br/>
Pointeur vers le chemin d’accès qualifié complet du document conteneur.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le document est enregistré avec succès ; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction pour créer ou ouvrir un fichier nommé pour enregistrer le document avec les DLL système OLE. Il est inutile d’appeler cette fonction si le document représente un élément incorporé.

Si vous utilisez `COleTemplateServer` dans votre application, `Register` est appelée pour vous par `COleLinkingDoc`d’implémentation de `OnNewDocument`, `OnOpenDocument`, et `OnSaveDocument`.

##  <a name="revoke"></a>  COleLinkingDoc::Revoke

Informe les DLL système OLE que le document n’est plus ouvert.

```
void Revoke();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour révoquer l’enregistrement du document avec les DLL système OLE.

Vous devez appeler cette fonction lors de la fermeture d’un fichier nommé, mais généralement, vous n’avez pas besoin d’appeler directement. `Revoke` est appelée pour vous par `COleLinkingDoc`d’implémentation de `OnCloseDocument`, `OnNewDocument`, `OnOpenDocument`, et `OnSaveDocument`.

## <a name="see-also"></a>Voir aussi

[Exemple MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate, classe](../../mfc/reference/cdoctemplate-class.md)
