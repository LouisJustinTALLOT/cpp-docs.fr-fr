---
title: Tables de dispatch | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d22c94513e80c4f353de9e10588f219a2d3be92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388067"
---
# <a name="dispatch-maps"></a>Tables de dispatch

OLE Automation fournit des méthodes pour appeler les méthodes et pour accéder aux propriétés entre les applications. Le mécanisme fourni par la bibliothèque Microsoft Foundation Class pour la distribution de ces requêtes est la « table de dispatch, » qui désigne les noms internes et externes des fonctions de l’objet et les propriétés, ainsi que les types de données des propriétés eux-mêmes et de arguments de fonction.

|Macro table de dispatch|Description|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Déclare qu’une table de dispatch servira à exposer des méthodes et des propriétés (doit être utilisé dans la déclaration de classe) d’une classe.|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Démarre la définition d’une table de dispatch.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Termine la définition d’une table de dispatch.|
|[DISP_FUNCTION](#disp_function)|Utilisé dans une table de dispatch pour définir une fonction d’automatisation OLE.|
|[DISP_PROPERTY](#disp_property)|Définit une propriété d’automation OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Définit une propriété d’automation OLE et le nomme les fonctions Get et Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Définit une propriété d’automation OLE avec notification.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Définit une propriété automation OLE qui prend des paramètres et les noms les fonctions Get et Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Rend une propriété existante à la valeur par défaut d’un objet.|

## <a name="declare_dispatch_map"></a>  DECLARE_DISPATCH_MAP

Si un `CCmdTarget`-classe dérivée dans votre programme prend en charge OLE Automation, que classe doit fournir une table de dispatch pour exposer ses méthodes et propriétés.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Notes

Utilisez le declare_dispatch_map (macro) à la fin de votre déclaration de classe. Ensuite, dans le. Fichier CPP qui définit les fonctions membres pour la classe, utilisez le begin_dispatch_map (macro). Puis inclure macro entrées pour chacune des méthodes exposées de votre classe et propriétés (DISP_FUNCTION DISP_PROPERTY et ainsi de suite). Enfin, utilisez l’end_dispatch_map (macro).

> [!NOTE]
> Si vous déclarez des membres après DECLARE_DISPATCH_MAP, vous devez spécifier un nouveau type d’accès ( **public**, **privé**, ou **protégé**) pour eux.

Les Assistants Application Assistant et code aident à créer des classes Automation et à la gestion des tables de dispatch. Pour plus d’informations sur les tables de dispatch, consultez [serveurs Automation](../../mfc/automation-servers.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="begin_dispatch_map"></a>  BEGIN_DISPATCH_MAP

Déclare la définition de votre table de dispatch.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Spécifie le nom de la classe qui possède cette table de dispatch.

*classe de base*<br/>
Spécifie le nom de classe de base de *theClass*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (.cpp) qui définit les fonctions membres pour votre classe, démarrer la table de dispatch avec le begin_dispatch_map (macro), ajouter des entrées de macro pour chacun de vos fonctions de distribution et les propriétés et terminer la table de dispatch avec la END_DISPATCH_ Macros de mappage.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="end_dispatch_map"></a>  END_DISPATCH_MAP

Met fin à la définition de votre table de dispatch.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Notes

Il doit être utilisé conjointement avec BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="disp_function"></a>  DISP_FUNCTION

Définit une fonction d’automatisation OLE dans une table de dispatch.

```cpp
DISP_FUNCTION(
  theClass,
  pszName,
  pfnMember,
  vtRetVal,
  vtsParams)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la fonction.

*pfnMember*<br/>
Nom de la fonction membre.

*vtRetVal*<br/>
Valeur spécifiant le type de retour de la fonction.

*vtsParams*<br/>
Une liste séparée par des espaces d’une ou plusieurs constantes spécifiant la liste des paramètres de la fonction.

### <a name="remarks"></a>Notes

Le *vtRetVal* argument est de type VARTYPE. Les valeurs possibles suivantes pour cet argument sont tirés du `VARENUM` énumération :

|Symbole|Type de retour|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Le *vtsParams* argument est une liste séparée par des espaces des valeurs à partir de la `VTS_*` constantes. Un ou plusieurs de ces valeurs séparées par des espaces (non par des virgules) spécifie la liste des paramètres de la fonction. Par exemple :

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

Spécifie une liste contenant un entier court suivi d’un pointeur vers un entier court.

Le `VTS_` constantes et leurs significations sont comme suit :

|Symbole|Type de paramètre|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` ou `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` ou `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__court\*__|
|VTS_PI4|__Long\*__|
|VTS_PR4|__Float\*__|
|VTS_PR8|__double\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Aucun paramètre|

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="disp_property"></a>  DISP_PROPERTY

Définit une propriété d’automation OLE dans une table de dispatch.

```cpp
DISP_PROPERTY(
  theClass,
  pszName,
  memberName,
  vtPropType)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*Nom de membre*<br/>
Nom de la variable de membre dans lequel la propriété est stockée.

*vtPropType*<br/>
Une valeur qui spécifie le type de propriété.

### <a name="remarks"></a>Notes

Le *vtPropType* argument est de type **VARTYPE**. Les valeurs possibles pour cet argument sont tirés de l’énumération VARENUM :

|Symbole|Type de propriété|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Quand un client externe modifie la propriété, la valeur de la variable de membre spécifiée par *memberName* change ; il n’existe aucune notification de la modification.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="disp_property_ex"></a>  DISP_PROPERTY_EX

Définit un nom et une propriété d’automation OLE les fonctions utilisées pour obtenir et définir la valeur de propriété dans une table de dispatch.

```cpp
DISP_PROPERTY_EX(
  theClass,
  pszName,
  memberGet,
  memberSet,
  vtPropType)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*memberGet*<br/>
Nom de la fonction de membre utilisée pour obtenir la propriété.

*jeu de membres*<br/>
Nom de la fonction membre permet de définir la propriété.

*vtPropType*<br/>
Une valeur qui spécifie le type de propriété.

### <a name="remarks"></a>Notes

Le *memberGet* et *memberSet* fonctions ont des signatures déterminés par le *vtPropType* argument. Le *memberGet* fonction n’accepte aucun argument et retourne une valeur du type spécifié par *vtPropType*. Le *memberSet* fonction accepte un argument de type spécifié par *vtPropType* et ne retourne rien.

Le *vtPropType* argument est de type VARTYPE. Les valeurs possibles pour cet argument sont tirés de l’énumération VARENUM. Pour obtenir la liste de ces valeurs, consultez les notes relatives à la *vtRetVal* paramètre dans [DISP_FUNCTION](#disp_function). Notez que VT_EMPTY, répertoriés dans la section Notes DISP_FUNCTION, n’est pas autorisée comme un type de données de propriété.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="disp_property_notify"></a>  DISP_PROPERTY_NOTIFY

Définit une propriété d’automation OLE avec notification dans une table de dispatch.

```cpp
DISP_PROPERTY_NOTIFY(
  theClass,
  szExternalName,
  memberName,
  pfnAfterSet,
  vtPropType)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe.

*szExternalName*<br/>
Nom externe de la propriété.

*Nom de membre*<br/>
Nom de la variable de membre dans lequel la propriété est stockée.

*pfnAfterSet*<br/>
Nom de la fonction de notification pour *szExternalName*.

*vtPropType*<br/>
Une valeur qui spécifie le type de propriété.

### <a name="remarks"></a>Notes

Contrairement aux propriétés définies avec DISP_PROPERTY, une propriété définie avec DISP_PROPERTY_NOTIFY appelle automatiquement la fonction spécifiée par *pfnAfterSet* lorsque la propriété est modifiée.

Le *vtPropType* argument est de type VARTYPE. Les valeurs possibles pour cet argument sont tirés de l’énumération VARENUM :

|Symbole|Type de propriété|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="disp_property_param"></a>  DISP_PROPERTY_PARAM

Définit une propriété accédée avec différentes `Get` et `Set` fonctions membres.

```cpp
DISP_PROPERTY_PARAM(
  theClass,
  pszExternalName,
  pfnGet,
  pfnSet,
  vtPropType,
  vtsParams)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe.

*pszExternalName*<br/>
Nom externe de la propriété.

*pfnGet*<br/>
Nom de la fonction de membre utilisée pour obtenir la propriété.

*pfnSet*<br/>
Nom de la fonction membre permet de définir la propriété.

*vtPropType*<br/>
Une valeur qui spécifie le type de propriété.

*vtsParams*<br/>
Une chaîne de séparées par des espaces `VTS_*` variant les types de paramètres, un pour chaque paramètre.

### <a name="remarks"></a>Notes

Contrairement à la macro DISP_PROPERTY_EX, cette macro vous permet de spécifier une liste de paramètres pour la propriété. Cela est utile pour implémenter des propriétés qui sont indexées ou paramétrées.

### <a name="example"></a>Exemple

Considérez la déclaration suivante de get et définir des fonctions qui permettent à l’utilisateur de demander une ligne spécifique et une colonne lorsque vous accédez à la propriété de membre :

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Ils correspondent à la macro DISP_PROPERTY_PARAM suivante dans la table de dispatch de contrôle :

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Autre exemple, envisagez la méthode get suivante et définir des fonctions de membre :

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Ils correspondent à la macro DISP_PROPERTY_PARAM suivante dans la table de dispatch de contrôle :

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="disp_defvalue"></a>  DISP_DEFVALUE

Rend une propriété existante à la valeur par défaut d’un objet.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété qui représente la « valeur » de l’objet.

### <a name="remarks"></a>Notes

À l’aide d’une valeur par défaut peut faire de la programmation de votre objet automation plus simple pour les applications Visual Basic.

La valeur « par défaut » de votre objet est la propriété qui est récupérée ou définie lorsqu’une référence à un objet ne spécifie pas une propriété ou une fonction membre.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
