---
description: 'En savoir plus sur : classe COleLinkingDoc'
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
ms.openlocfilehash: 10cf9bb81c4cbbd324b95a13dc2fa44548266583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226907"
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
|[COleLinkingDoc :: Register](#register)|Inscrit le document avec les DLL système OLE.|
|[COleLinkingDoc :: Revoke](#revoke)|Révoque l’inscription du document.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Recherche l’élément incorporé spécifié.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Recherche l’élément lié spécifié.|

## <a name="remarks"></a>Notes

Une application conteneur qui prend en charge la liaison aux éléments incorporés est appelée « conteneur de liens ». L’exemple d’application [OCLIENT](../../overview/visual-cpp-samples.md) est un exemple de conteneur de liens.

Quand la source d’un élément lié est un élément incorporé dans un autre document, le document qui le contient doit être chargé pour que l’élément incorporé soit modifié. Pour cette raison, un conteneur de liens doit pouvoir être lancé par une autre application conteneur lorsque l’utilisateur souhaite modifier la source d’un élément lié. Votre application doit également utiliser la classe [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) pour pouvoir créer des documents quand elle est lancée par programmation.

Pour transformer votre conteneur en conteneur de liens, dérivez votre classe de document à partir `COleLinkingDoc` de la place de [COleDocument](../../mfc/reference/coledocument-class.md). Comme pour tout autre conteneur OLE, vous devez concevoir votre classe pour stocker les données natives de l’application ainsi que les éléments incorporés ou liés. En outre, vous devez concevoir des structures de données pour le stockage de vos données natives. Si vous définissez une `CDocItem` classe dérivée de pour les données natives de votre application, vous pouvez utiliser l’interface définie par `COleDocument` pour stocker vos données natives ainsi que vos données OLE.

Pour permettre à votre application d’être lancée par programme par un autre conteneur, déclarez un `COleTemplateServer` objet en tant que membre de la `CWinApp` classe dérivée de votre application :

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

Dans la `InitInstance` fonction membre de votre `CWinApp` classe dérivée de, créez un modèle de document et spécifiez votre `COleLinkingDoc` classe dérivée de comme classe de document :

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Connectez votre `COleTemplateServer` objet à vos modèles de document en appelant la fonction membre de l’objet `ConnectTemplate` et enregistrez tous les objets de classe auprès du système OLE en appelant `COleTemplateServer::RegisterAll` :

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Pour obtenir un exemple de `CWinApp` définition et de fonction de classe dérivée `InitInstance` , consultez OCLIENT. H et OCLIENT. CPP dans l’exemple MFC [OCLIENT](../../overview/visual-cpp-samples.md).

Pour plus d’informations sur l’utilisation de `COleLinkingDoc` , consultez l’article [conteneurs : implémentation d’un conteneur](../../mfc/containers-implementing-a-container.md) et de [conteneurs : fonctionnalités avancées](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a> COleLinkingDoc::COleLinkingDoc

Construit un `COleLinkingDoc` objet sans commencer à communiquer avec les DLL système OLE.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Notes

Vous devez appeler la `Register` fonction membre pour informer OLE que le document est ouvert.

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a> COleLinkingDoc::OnFindEmbeddedItem

Appelée par l’infrastructure pour déterminer si le document contient un élément OLE incorporé avec le nom spécifié.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName*<br/>
Pointeur vers le nom de l’élément OLE incorporé demandé.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément spécifié ; NULL si l’élément est introuvable.

### <a name="remarks"></a>Notes

L’implémentation par défaut recherche dans la liste d’éléments incorporés un élément portant le nom spécifié (la comparaison de noms respecte la casse). Remplacez cette fonction si vous disposez de votre propre méthode de stockage ou de dénomination des éléments OLE incorporés.

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a> COleLinkingDoc::OnGetLinkedItem

Appelé par l’infrastructure pour vérifier si le document contient un élément de serveur lié portant le nom spécifié.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName*<br/>
Pointeur vers le nom de l’élément OLE lié demandé.

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’élément spécifié ; NULL si l’élément est introuvable.

### <a name="remarks"></a>Notes

L’implémentation par défaut `COleLinkingDoc` retourne toujours la valeur null. Cette fonction est substituée dans la classe dérivée `COleServerDoc` pour effectuer une recherche dans la liste des éléments de serveur OLE d’un élément lié portant le nom spécifié (la comparaison de noms respecte la casse). Substituez cette fonction si vous avez implémenté votre propre méthode de stockage ou d’extraction d’éléments de serveur liés.

## <a name="colelinkingdocregister"></a><a name="register"></a> COleLinkingDoc :: Register

Informe les DLL système OLE que le document est ouvert.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Paramètres

*pFactory*<br/>
Pointeur vers un objet de fabrique OLE (peut être NULL).

*lpszPathName*<br/>
Pointeur vers le chemin d’accès qualifié complet du document conteneur.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le document est correctement inscrit ; Sinon, 0.

### <a name="remarks"></a>Notes

Appelez cette fonction lors de la création ou de l’ouverture d’un fichier nommé pour inscrire le document auprès des DLL système OLE. Il n’est pas nécessaire d’appeler cette fonction si le document représente un élément incorporé.

Si vous utilisez `COleTemplateServer` dans votre application, `Register` est appelé pour vous par `COleLinkingDoc` l’implémentation de, de et de `OnNewDocument` `OnOpenDocument` `OnSaveDocument` .

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a> COleLinkingDoc :: Revoke

Informe les DLL système OLE que le document n’est plus ouvert.

```cpp
void Revoke();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour révoquer l’inscription du document avec les DLL système OLE.

Vous devez appeler cette fonction lors de la fermeture d’un fichier nommé, mais vous n’avez généralement pas besoin de l’appeler directement. `Revoke` est appelé pour vous par `COleLinkingDoc` l’implémentation de, de, de `OnCloseDocument` `OnNewDocument` et de `OnOpenDocument` `OnSaveDocument` .

## <a name="see-also"></a>Voir aussi

[Exemple MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate (classe)](../../mfc/reference/cdoctemplate-class.md)
