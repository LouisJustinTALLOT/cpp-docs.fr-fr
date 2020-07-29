---
title: Tables de dispatch
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 24921f2da404a2e5103d9a3cd2abba03109f0681
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222808"
---
# <a name="dispatch-maps"></a>Tables de dispatch

OLE Automation permet d’appeler des méthodes et d’accéder aux propriétés d’une application à l’autre. Le mécanisme fourni par le bibliothèque MFC (Microsoft Foundation Class) pour distribuer ces requêtes est la « table de dispatch », qui désigne les noms internes et externes des fonctions et des propriétés d’objet, ainsi que les types de données des propriétés elles-mêmes et des arguments de fonction.

|Macro de table de dispatch|Description|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Déclare qu’une table de dispatch sera utilisée pour exposer les méthodes et les propriétés d’une classe (doit être utilisé dans la déclaration de classe).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Démarre la définition d’une table de dispatch.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Termine la définition d’une table de dispatch.|
|[DISP_FUNCTION](#disp_function)|Utilisé dans une table de dispatch pour définir une fonction OLE Automation.|
|[DISP_PROPERTY](#disp_property)|Définit une propriété OLE Automation.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Définit une propriété OLE Automation et nomme les fonctions d’extraction et de définition.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Définit une propriété OLE Automation avec notification.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Définit une propriété OLE Automation qui accepte des paramètres et nomme les fonctions d’extraction et de définition.|
|[DISP_DEFVALUE](#disp_defvalue)|Fait d’une propriété existante la valeur par défaut d’un objet.|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

Si une `CCmdTarget` classe dérivée de votre programme prend en charge OLE Automation, cette classe doit fournir un mappage de dispatch pour exposer ses méthodes et ses propriétés.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Notes

Utilisez la macro DECLARE_DISPATCH_MAP à la fin de votre déclaration de classe. Puis, dans la. CPP qui définit les fonctions membres de la classe, utilisez la macro BEGIN_DISPATCH_MAP. Incluez ensuite des entrées de macro pour chaque méthode et propriété exposées de votre classe (DISP_FUNCTION, DISP_PROPERTY, etc.). Enfin, utilisez la macro END_DISPATCH_MAP.

> [!NOTE]
> Si vous déclarez des membres après DECLARE_DISPATCH_MAP, vous devez spécifier un nouveau type d’accès ( **`public`** , **`private`** ou **`protected`** ) pour eux.

L’Assistant Application et les assistants code aident à créer des classes Automation et à gérer les tables de dispatch. Pour plus d’informations sur les tables de dispatch, consultez [Serveurs Automation](../../mfc/automation-servers.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Déclare la définition de votre table de dispatch.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Spécifie le nom de la classe qui possède ce mappage de dispatch.

*baseClass*<br/>
Spécifie le nom de la classe de base de *les*.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (. cpp) qui définit les fonctions membres pour votre classe, démarrez la table de dispatch avec la macro BEGIN_DISPATCH_MAP, ajoutez des entrées de macro pour chacune de vos fonctions et propriétés de répartition, puis complétez la table de dispatch avec la macro END_DISPATCH_MAP.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

Termine la définition de votre table de dispatch.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Notes

Elle doit être utilisée conjointement avec BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

Définit une fonction OLE Automation dans une table de dispatch.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la fonction.

*pfnMember*<br/>
Nom de la fonction membre.

*vtRetVal*<br/>
Valeur qui spécifie le type de retour de la fonction.

*vtsParams*<br/>
Liste séparée par des espaces d’une ou de plusieurs constantes spécifiant la liste de paramètres de la fonction.

### <a name="remarks"></a>Notes

L’argument *vtRetVal* est de type VarType. Les valeurs possibles suivantes pour cet argument sont extraites de l' `VARENUM` énumération :

|Symbole|Type de retour|
|------------|-----------------|
|VT_EMPTY|**`void`**|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

L’argument *vtsParams* est une liste de valeurs séparées par des espaces des `VTS_*` constantes. Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste de paramètres de la fonction. Par exemple,

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

spécifie une liste contenant un entier Short suivi d’un pointeur vers un entier bref.

Les `VTS_` constantes et leurs significations sont les suivantes :

|Symbole|Type de paramètre|
|------------|--------------------|
|VTS_I2|**`short`**|
|VTS_I4|**`long`**|
|VTS_R4|**`float`**|
|VTS_R8|**`double`**|
|VTS_CY|`const CY` ou `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` ou `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__short\*__|
|VTS_PI4|__long\*__|
|VTS_PR4|__dissocié\*__|
|VTS_PR8|__Cliquer\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Aucun paramètre|

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_property"></a><a name="disp_property"></a>DISP_PROPERTY

Définit une propriété OLE Automation dans une table de dispatch.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*memberName*<br/>
Nom de la variable membre dans laquelle la propriété est stockée.

*vtPropType*<br/>
Valeur qui spécifie le type de la propriété.

### <a name="remarks"></a>Notes

L’argument *vtPropType* est de type **VarType**. Les valeurs possibles pour cet argument sont extraites de l’énumération VARENUM :

|Symbole|Type de propriété|
|------------|-----------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Lorsqu’un client externe modifie la propriété, la valeur de la variable membre spécifiée par *MemberName* change ; Il n’y a aucune notification de la modification.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

Définit une propriété OLE Automation et nomme les fonctions utilisées pour obtenir et définir la valeur de la propriété dans une table de dispatch.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété.

*memberGet*<br/>
Nom de la fonction membre utilisée pour accéder à la propriété.

*PEL*<br/>
Nom de la fonction membre utilisée pour définir la propriété.

*vtPropType*<br/>
Valeur qui spécifie le type de la propriété.

### <a name="remarks"></a>Notes

Les fonctions *memberGet* et *memberSet* ont des signatures déterminées par l’argument *vtPropType* . La fonction *memberGet* n’accepte aucun argument et retourne une valeur du type spécifié par *vtPropType*. La fonction *memberSet* accepte un argument du type spécifié par *vtPropType* et ne retourne rien.

L’argument *vtPropType* est de type VarType. Les valeurs possibles pour cet argument sont extraites de l’énumération VARENUM. Pour obtenir la liste de ces valeurs, consultez les notes relatives au paramètre *vtRetVal* dans [DISP_FUNCTION](#disp_function). Notez que VT_EMPTY, listé dans les notes de DISP_FUNCTION, n’est pas autorisé en tant que type de données de propriété.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Définit une propriété OLE Automation avec notification dans une table de dispatch.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*szExternalName*<br/>
Nom externe de la propriété.

*memberName*<br/>
Nom de la variable membre dans laquelle la propriété est stockée.

*pfnAfterSet*<br/>
Nom de la fonction de notification pour *szExternalName*.

*vtPropType*<br/>
Valeur qui spécifie le type de la propriété.

### <a name="remarks"></a>Notes

Contrairement aux propriétés définies avec DISP_PROPERTY, une propriété définie avec DISP_PROPERTY_NOTIFY appellera automatiquement la fonction spécifiée par *pfnAfterSet* lorsque la propriété est modifiée.

L’argument *vtPropType* est de type VarType. Les valeurs possibles pour cet argument sont extraites de l’énumération VARENUM :

|Symbole|Type de propriété|
|------------|-----------------------|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_property_param"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Définit une propriété accessible avec des `Get` `Set` fonctions membres et distinctes.

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

*Les*<br/>
Nom de la classe.

*pszExternalName*<br/>
Nom externe de la propriété.

*pfnGet*<br/>
Nom de la fonction membre utilisée pour accéder à la propriété.

*pfnSet*<br/>
Nom de la fonction membre utilisée pour définir la propriété.

*vtPropType*<br/>
Valeur qui spécifie le type de la propriété.

*vtsParams*<br/>
Chaîne de `VTS_*` types de paramètres variant séparés par des espaces, une pour chaque paramètre.

### <a name="remarks"></a>Notes

Contrairement à la macro DISP_PROPERTY_EX, cette macro vous permet de spécifier une liste de paramètres pour la propriété. Cela est utile pour implémenter des propriétés indexées ou paramétrées.

### <a name="example"></a>Exemple

Considérez la déclaration suivante des fonctions membres obtenir et définir qui permettent à l’utilisateur de demander une ligne et une colonne spécifiques lors de l’accès à la propriété :

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Celles-ci correspondent à la macro DISP_PROPERTY_PARAM suivante dans le mappage de dispatch de contrôle :

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

En guise d’autre exemple, considérez les fonctions membres suivantes :

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Celles-ci correspondent à la macro DISP_PROPERTY_PARAM suivante dans le mappage de dispatch de contrôle :

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

Fait d’une propriété existante la valeur par défaut d’un objet.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe.

*pszName*<br/>
Nom externe de la propriété qui représente la « valeur » de l’objet.

### <a name="remarks"></a>Notes

L’utilisation d’une valeur par défaut permet de simplifier la programmation de votre objet Automation pour les applications Visual Basic.

La « valeur par défaut » de votre objet est la propriété qui est extraite ou définie quand une référence à un objet ne spécifie pas une propriété ou une fonction membre.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
