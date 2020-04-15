---
title: Fabriques de classes et gestion des licences
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: e3fed6520cdbe0fd964e4e80e7c9ed9b78296d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372308"
---
# <a name="class-factories-and-licensing"></a>Fabriques de classes et gestion des licences

Pour créer une instance de votre contrôle OLE, une application de conteneurs appelle une fonction membre de l’usine de classe du contrôle. Parce que votre contrôle est un objet OLE réel, l’usine de classe est responsable de créer des instances de votre contrôle. Chaque classe de contrôle OLE doit avoir une usine de classe.

Une autre caractéristique importante des contrôles OLE est leur capacité à faire respecter une licence. ControlWizard vous permet d’intégrer des licences lors de la création de votre projet de contrôle. Pour plus d’informations sur les licences de contrôle, voir l’article [ActiveX Controls: Licensing An ActiveX Control](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

Le tableau suivant répertorie plusieurs macros et fonctions utilisées pour déclarer et mettre en œuvre l’usine de classe de votre contrôle et pour obtenir une licence de votre contrôle.

### <a name="class-factories-and-licensing"></a>Fabriques de classes et gestion des licences

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Déclare l’usine de classe pour une page de contrôle ou de propriété OLE.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implémente la `GetClassID` fonction du contrôle et déclare un exemple de l’usine de classe.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Commence la déclaration de toutes les fonctions de licence.|
|[END_OLEFACTORY](#end_olefactory)|Termine la déclaration de toute fonction de licence.|
|[AfxVerifyLicFile](#afxverifylicfile)|Vérifie si un contrôle est autorisé à être utilisé sur un ordinateur particulier.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Déclare une usine de `GetClassID` classe et la fonction membre de votre classe de contrôle.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle.

### <a name="remarks"></a>Notes

Utilisez cette macro dans le fichier d’en-tête de la classe de contrôle pour un contrôle qui ne prend pas en charge les licences.

Notez que cette macro sert le même but que l’échantillon de code suivant :

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

Implémente l’usine de classe de votre contrôle et la fonction membre [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) de votre classe de contrôle.

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
Le nom de la classe de page de propriété de contrôle.

*external_name*<br/>
Le nom de l’objet exposé aux applications.

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
Composants du CLSID de la classe. Pour plus d’informations sur ces paramètres, voir les remarques pour [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Notes

Cette macro doit apparaître dans le fichier d’implémentation de toute classe de contrôle qui utilise la macro DECLARE_OLECREATE_EX ou les macros BEGIN_OLEFACTORY et END_OLEFACTORY. Le nom externe est l’identifiant du contrôle OLE qui est exposé à d’autres applications. Les conteneurs utilisent ce nom pour demander un objet de cette classe de contrôle.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Commence la déclaration de votre usine de classe dans le fichier d’en-tête de votre classe de contrôle.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Précise le nom de la classe de contrôle dont il s’agit d’usine de classe.

### <a name="remarks"></a>Notes

Les déclarations des fonctions de licence d’usine de classe devraient commencer immédiatement après BEGIN_OLEFACTORY.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="end_olefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY

Termine la déclaration de l’usine de classe de votre contrôle.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle dont l’usine de classe c’est.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a>AfxVerifyLicFile

Appelez cette fonction pour vérifier que `pszLicFileName` le fichier de licence nommé par est valide pour le contrôle OLE.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Paramètres

*hInstance*<br/>
La poignée d’instance de la DLL associée au contrôle autorisé.

*pszLicFileName*<br/>
Indique une chaîne de caractères non terminée contenant le nom de fichier de licence.

*pszLicFileContents*<br/>
Points à une séquence d’enders qui doit correspondre à la séquence trouvée au début du fichier de licence.

*Cch*<br/>
Nombre de *caractères dans pszLicFileContents*.

### <a name="return-value"></a>Valeur de retour

Nonzero si le fichier de licence existe et commence avec la séquence de caractères dans *pszLicFileContents*; sinon 0.

### <a name="remarks"></a>Notes

Si *le cch* est de -1, cette fonction utilise :

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
