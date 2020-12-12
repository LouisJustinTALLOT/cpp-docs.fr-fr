---
description: 'En savoir plus sur : fabriques de classes et gestion des licences'
title: Fabriques de classes et gestion des licences
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 7470a5828df358a28db5a30832f98314e09a133e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236839"
---
# <a name="class-factories-and-licensing"></a>Fabriques de classes et gestion des licences

Pour créer une instance de votre contrôle OLE, une application conteneur appelle une fonction membre de la fabrique de classe du contrôle. Étant donné que votre contrôle est un objet OLE réel, la fabrique de classe est chargée de créer des instances de votre contrôle. Chaque classe de contrôle OLE doit avoir une fabrique de classe.

Une autre fonctionnalité importante des contrôles OLE est leur capacité à appliquer une licence. ControlWizard vous permet d’incorporer des licences lors de la création de votre projet de contrôle. Pour plus d’informations sur le contrôle des licences, consultez l’article [contrôles ActiveX : gestion des licences d’un contrôle ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

Le tableau suivant répertorie plusieurs macros et fonctions utilisées pour déclarer et implémenter la fabrique de classe de votre contrôle et la licence de votre contrôle.

### <a name="class-factories-and-licensing"></a>Fabriques de classes et gestion des licences

|Macro ou fonction|Description|
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Déclare la fabrique de classe pour un contrôle OLE ou une page de propriétés.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implémente la fonction du contrôle `GetClassID` et déclare une instance de la fabrique de classe.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Commence la déclaration de toutes les fonctions de licence.|
|[END_OLEFACTORY](#end_olefactory)|Met fin à la déclaration de toutes les fonctions de licence.|
|[AfxVerifyLicFile](#afxverifylicfile)|Vérifie si un contrôle est concédé sous licence pour une utilisation sur un ordinateur particulier.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a> DECLARE_OLECREATE_EX

Déclare une fabrique de classes et la `GetClassID` fonction membre de votre classe de contrôle.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle.

### <a name="remarks"></a>Notes

Utilisez cette macro dans le fichier d’en-tête de la classe de contrôle pour un contrôle qui ne prend pas en charge la gestion des licences.

Notez que cette macro remplit la même fonction que l’exemple de code suivant :

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a> IMPLEMENT_OLECREATE_EX

Implémente la fabrique de classe de votre contrôle et la fonction membre [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) de votre classe de contrôle.

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de la page de propriétés du contrôle.

*external_name*<br/>
Nom de l’objet exposé aux applications.

*l, W1, W2, B1, B2, B3, B4, B5, B6, B7, B8*<br/>
Composants du CLSID de la classe. Pour plus d’informations sur ces paramètres, consultez les notes relatives à [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Notes

Cette macro doit apparaître dans le fichier d’implémentation pour toute classe de contrôle qui utilise la macro DECLARE_OLECREATE_EX ou les macros BEGIN_OLEFACTORY et END_OLEFACTORY. Le nom externe est l’identificateur du contrôle OLE qui est exposé à d’autres applications. Les conteneurs utilisent ce nom pour demander un objet de cette classe de contrôle.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a> BEGIN_OLEFACTORY

Commence la déclaration de votre fabrique de classe dans le fichier d’en-tête de votre classe de contrôle.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Spécifie le nom de la classe de contrôle dont la fabrique de classe est.

### <a name="remarks"></a>Notes

Les déclarations des fonctions de gestion de licences de la fabrique de classes doivent commencer immédiatement après BEGIN_OLEFACTORY.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="end_olefactory"></a><a name="end_olefactory"></a> END_OLEFACTORY

Termine la déclaration de la fabrique de classe de votre contrôle.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle dont la fabrique de classe est.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a> AfxVerifyLicFile

Appelez cette fonction pour vérifier que le fichier de licence nommé par `pszLicFileName` est valide pour le contrôle OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
Handle d’instance de la DLL associée au contrôle sous licence.

*pszLicFileName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui contient le nom du fichier de licence.

*pszLicFileContents*<br/>
Pointe vers une séquence d’octets qui doit correspondre à la séquence trouvée au début du fichier de licence.

*CCH*<br/>
Nombre de caractères dans *pszLicFileContents*.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le fichier de licence existe et commence par la séquence de caractères dans *pszLicFileContents*; Sinon, 0.

### <a name="remarks"></a>Notes

Si *CCH* est-1, cette fonction utilise :

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
