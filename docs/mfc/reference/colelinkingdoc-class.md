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
ms.openlocfilehash: 1fad986b7e7304075cacb0b5ced9feeb8af4664f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753841"
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
|[COleLinkingDoc::Enregistrement](#register)|Enregistre le document avec le système OLE DLLs.|
|[COleLinkingDoc::Revoke](#revoke)|Révoque l’enregistrement du document.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Trouve l’élément intégré spécifié.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Trouve l’élément lié spécifié.|

## <a name="remarks"></a>Notes

Une application de conteneurs qui prend en charge la liaison vers les articles embarqués est appelée un « conteneur de liaison ». [L’application d’échantillon OCLIENT](../../overview/visual-cpp-samples.md) est un exemple d’un conteneur de liaison.

Lorsque la source d’un élément lié est un élément intégré dans un autre document, ce document contenant doit être chargé pour que l’élément intégré soit modifié. Pour cette raison, un conteneur de liaison doit pouvoir être lancé par une autre application de conteneur lorsque l’utilisateur veut modifier la source d’un élément lié. Votre application doit également utiliser la classe [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) afin qu’elle puisse créer des documents lorsqu’elle est lancée sur le plan programmatique.

Pour faire de votre conteneur un conteneur `COleLinkingDoc` de liaison, dérivez votre classe de documents au lieu de [COleDocument](../../mfc/reference/coledocument-class.md). Comme pour tout autre conteneur OLE, vous devez concevoir votre classe pour stocker les données natives de l’application ainsi que les éléments intégrés ou liés. En outre, vous devez concevoir des structures de données pour stocker vos données natives. Si vous `CDocItem`définissez une classe dérivée pour les données natives `COleDocument` de votre application, vous pouvez utiliser l’interface définie par le stockage de vos données natives ainsi que vos données OLE.

Pour permettre le lancement de votre demande sur `COleTemplateServer` le plan programmatique par `CWinApp`un autre conteneur, déclarez un objet en tant que membre de la classe dérivée de votre application :

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

Dans `InitInstance` la fonction `CWinApp`membre de votre classe dérivée, `COleLinkingDoc`créez un modèle de document et spécifiez votre classe dérivée comme classe de documents :

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Connectez `COleTemplateServer` votre objet à vos modèles de `ConnectTemplate` documents en appelant la fonction membre de `COleTemplateServer::RegisterAll`l’objet, et enregistrez tous les objets de classe avec le système OLE en appelant :

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Pour une `CWinApp`définition et `InitInstance` une fonction de classe dérivées d’un échantillon, voir OCLIENT. H et OCLIENT. RPC dans l’échantillon [OCLIENT](../../overview/visual-cpp-samples.md)de MFC .

Pour plus d’informations sur l’utilisation `COleLinkingDoc`, voir les articles [Conteneurs: Mise en œuvre d’un conteneur](../../mfc/containers-implementing-a-container.md) et [conteneurs: Fonctionnalités avancées](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a>COleLinkingDoc::COleLinkingDoc

Construit un `COleLinkingDoc` objet sans commencer les communications avec le système OLE DLLs.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Notes

Vous devez `Register` appeler la fonction membre pour informer OLE que le document est ouvert.

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a>COleLinkingDoc::OnFindEmbeddedItem

Appelé par le cadre pour déterminer si le document contient un élément OLE intégré avec le nom spécifié.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName (en)*<br/>
Pointeur sur le nom de l’élément OLE intégré demandé.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément spécifié; NULL si l’article n’est pas trouvé.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut recherche la liste des éléments intégrés pour un élément avec le nom spécifié (la comparaison de nom est sensible au cas). Remplacez cette fonction si vous avez votre propre méthode de stockage ou de nommage d’éléments OLE intégrés.

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a>COleLinkingDoc::OnGetLinkedItem

Appelé par le cadre pour vérifier si le document contient un élément serveur lié avec le nom spécifié.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Paramètres

*lpszItemName (en)*<br/>
Pointeur sur le nom de l’élément OLE lié demandé.

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’élément spécifié; NULL si l’article n’est pas trouvé.

### <a name="remarks"></a>Notes

L’implémentation par défaut `COleLinkingDoc` renvoie toujours NULL. Cette fonction est remplace dans `COleServerDoc` la classe dérivée pour rechercher la liste des éléments du serveur OLE pour un élément lié au nom spécifié (la comparaison de nom est sensible au cas). Remplacez cette fonction si vous avez implémenté votre propre méthode de stockage ou de récupération d’éléments de serveur liés.

## <a name="colelinkingdocregister"></a><a name="register"></a>COleLinkingDoc::Enregistrement

Informe le système OLE DLLs que le document est ouvert.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Paramètres

*pFactory*<br/>
Pointeur vers un objet d’usine OLE (peut être NULL).

*lpszPathName (en)*<br/>
Pointeur sur la trajectoire entièrement qualifiée du document de conteneur.

### <a name="return-value"></a>Valeur de retour

Nonzero si le document est enregistré avec succès; sinon 0.

### <a name="remarks"></a>Notes

Appelez cette fonction lors de la création ou de l’ouverture d’un fichier nommé pour enregistrer le document avec le système OLE DLLs. Il n’est pas nécessaire d’appeler cette fonction si le document représente un élément intégré.

Si vous `COleTemplateServer` utilisez dans `Register` votre application, `COleLinkingDoc`est appelé `OnNewDocument`pour `OnOpenDocument`vous `OnSaveDocument`par la mise en œuvre de , , , et .

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a>COleLinkingDoc::Revoke

Informe le système OLE DLLs que le document n’est plus ouvert.

```cpp
void Revoke();
```

### <a name="remarks"></a>Notes

Appelez cette fonction pour révoquer l’enregistrement du document auprès des DLL du système OLE.

Vous devez appeler cette fonction lors de la fermeture d’un fichier nommé, mais vous n’avez généralement pas besoin de l’appeler directement. `Revoke`est appelé pour `COleLinkingDoc`vous par `OnCloseDocument` `OnNewDocument`la `OnOpenDocument`mise `OnSaveDocument`en œuvre de , , , et .

## <a name="see-also"></a>Voir aussi

[Échantillon MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
