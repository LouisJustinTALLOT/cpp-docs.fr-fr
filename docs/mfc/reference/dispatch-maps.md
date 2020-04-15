---
title: Tables de dispatch
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 59dd8c7a7b0b930ffdb68fd96410fd73aeb02e81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365754"
---
# <a name="dispatch-maps"></a>Tables de dispatch

OLE Automation fournit des moyens d’appeler les méthodes et d’accéder aux propriétés entre les applications. Le mécanisme fourni par la Microsoft Foundation Class Library pour l’envoi de ces demandes est la « carte d’expédition », qui désigne les noms internes et externes des fonctions et des propriétés des objets, ainsi que les types de données des propriétés elles-mêmes et des arguments de fonction.

|Carte d’expédition macro|Description|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Déclare qu’une carte de répartition sera utilisée pour exposer les méthodes et les propriétés d’une classe (doit être utilisée dans la déclaration de classe).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Commence la définition d’une carte de répartition.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Termine la définition d’une carte de répartition.|
|[DISP_FUNCTION](#disp_function)|Utilisé dans une carte d’expédition pour définir une fonction d’automatisation OLE.|
|[DISP_PROPERTY](#disp_property)|Définit une propriété d’automatisation OLE.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Définit une propriété d’automatisation OLE et nomme les fonctions Get and Set.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Définit une propriété d’automatisation OLE avec notification.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Définit une propriété d’automatisation OLE qui prend des paramètres et nomme les fonctions Get and Set.|
|[DISP_DEFVALUE](#disp_defvalue)|Fait d’une propriété existante la valeur par défaut d’un objet.|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

Si `CCmdTarget`une classe dérivée de votre programme prend en charge OLE Automation, cette classe doit fournir une carte de répartition pour exposer ses méthodes et propriétés.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Notes

Utilisez la DECLARE_DISPATCH_MAP macro à la fin de votre déclaration de classe. Puis, dans le . Fichier du RPC qui définit les fonctions des membres pour la classe, utilisez le BEGIN_DISPATCH_MAP macro. Ensuite, incluez des entrées macro pour chacune des méthodes et propriétés exposées de votre classe (DISP_FUNCTION, DISP_PROPERTY, et ainsi de suite). Enfin, utilisez la macro END_DISPATCH_MAP.

> [!NOTE]
> Si vous déclarez des membres après DECLARE_DISPATCH_MAP, vous devez spécifier un nouveau type d’accès **(public,** **privé**ou **protégé)** pour eux.

L’Assistant d’Application et les assistants de code aident à créer des classes d’automatisation et à maintenir des cartes d’expédition. Pour plus d’informations sur les cartes de répartition, voir [Serveurs d’automatisation](../../mfc/automation-servers.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Déclare la définition de votre carte de répartition.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Précise le nom de la classe qui possède cette carte de répartition.

*Baseclass*<br/>
Spécifie le nom de classe de base de *la Classe*.

### <a name="remarks"></a>Notes

Dans le fichier de mise en œuvre (.cpp) qui définit les fonctions des membres pour votre classe, démarrez la carte de répartition avec la BEGIN_DISPATCH_MAP macro, ajoutez des entrées macro pour chacune de vos fonctions et propriétés de répartition, et complétez la carte de répartition avec la END_DISPATCH_MAP macro.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

Termine la définition de votre carte de répartition.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Notes

Il doit être utilisé en conjonction avec BEGIN_DISPATCH_MAP.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

Définit une fonction d’automatisation OLE dans une carte de répartition.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Nom de la classe.

*pszName (en)*<br/>
Nom externe de la fonction.

*pfnMember*<br/>
Nom de la fonction membre.

*vtRetVal*<br/>
Une valeur spécifiant le type de retour de la fonction.

*vtsParams*<br/>
Une liste séparée par l’espace d’une ou plusieurs constantes spécifiant la liste des paramètres de la fonction.

### <a name="remarks"></a>Notes

*L’argument vtRetVal* est de type VARTYPE. Les valeurs suivantes pour cet argument `VARENUM` sont tirées de l’énumération :

|Symbole|Type de retour|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**Long**|
|VT_R4|**Flotteur**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

*L’argument vtsParams* est une liste de `VTS_*` valeurs séparées par l’espace des constantes. Une ou plusieurs de ces valeurs séparées par des espaces (et non des virgules) spécifient la liste des paramètres de la fonction. Par exemple,

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

spécifie une liste contenant un integer court suivi d’un pointeur à un integer court.

Les `VTS_` constantes et leurs significations sont les suivantes :

|Symbole|Type de paramètre|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**Long**|
|VTS_R4|**Flotteur**|
|VTS_R8|**double**|
|VTS_CY|`const CY` ou `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` ou `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__Court\*__|
|VTS_PI4|__Long\*__|
|VTS_PR4|__Flotteur\*__|
|VTS_PR8|__Double\*__|
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

Définit une propriété d’automatisation OLE dans une carte de répartition.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Nom de la classe.

*pszName (en)*<br/>
Nom externe de la propriété.

*Membername*<br/>
Nom de la variable du membre dans laquelle la propriété est stockée.

*vtPropType (en)*<br/>
Une valeur spécifiant le type de propriété.

### <a name="remarks"></a>Notes

*L’argument vtPropType* est de type **VARTYPE**. Les valeurs possibles pour cet argument sont tirées de l’énumération VARENUM :

|Symbole|Type de propriété|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**Long**|
|VT_R4|**Flotteur**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Lorsqu’un client externe modifie la propriété, la valeur de la variable du membre spécifiée par *le membreName* change; il n’y a pas de notification de la modification.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

Définit une propriété d’automatisation OLE et nomme les fonctions utilisées pour obtenir et définir la valeur de la propriété dans une carte de répartition.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Nom de la classe.

*pszName (en)*<br/>
Nom externe de la propriété.

*membreGet*<br/>
Nom de la fonction membre utilisé pour obtenir la propriété.

*memberSet*<br/>
Nom de la fonction membre utilisé pour définir la propriété.

*vtPropType (en)*<br/>
Une valeur spécifiant le type de propriété.

### <a name="remarks"></a>Notes

Les fonctions *memberGet* et *memberSet* ont des signatures déterminées par l’argument *vtPropType.* La fonction *memberGet* ne prend aucun argument et renvoie une valeur du type spécifiée par *vtPropType*. La fonction *MemberSet* prend un argument du type spécifié par *vtPropType* et ne renvoie rien.

*L’argument vtPropType* est de type VARTYPE. Les valeurs possibles pour cet argument sont tirées de l’énumération VARENUM. Pour une liste de ces valeurs, voir les remarques pour le paramètre *vtRetVal* dans [DISP_FUNCTION](#disp_function). Notez que VT_EMPTY, énumérés dans les remarques DISP_FUNCTION, n’est pas permis comme type de données de propriété.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Définit une propriété d’automatisation OLE avec notification dans une carte de répartition.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Nom de la classe.

*szExternalName (en anglais)*<br/>
Nom externe de la propriété.

*Membername*<br/>
Nom de la variable du membre dans laquelle la propriété est stockée.

*pfnAfterSet*<br/>
Nom de la fonction de notification pour *szExternalName*.

*vtPropType (en)*<br/>
Une valeur spécifiant le type de propriété.

### <a name="remarks"></a>Notes

Contrairement aux propriétés définies avec DISP_PROPERTY, une propriété définie avec DISP_PROPERTY_NOTIFY appellera automatiquement la fonction spécifiée par *pfnAfterSet* lorsque la propriété est modifiée.

*L’argument vtPropType* est de type VARTYPE. Les valeurs possibles pour cet argument sont tirées de l’énumération VARENUM :

|Symbole|Type de propriété|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**Long**|
|VT_R4|**Flotteur**|
|VT_R8|**double**|
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

Définit une propriété accessible `Get` avec `Set` des fonctions séparées et membres.

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

*la Classe*<br/>
Nom de la classe.

*pszExternalName (en anglais)*<br/>
Nom externe de la propriété.

*pfnGet*<br/>
Nom de la fonction membre utilisé pour obtenir la propriété.

*pfnSet (en anglais)*<br/>
Nom de la fonction membre utilisé pour définir la propriété.

*vtPropType (en)*<br/>
Une valeur spécifiant le type de propriété.

*vtsParams*<br/>
Une chaîne de `VTS_*` types de paramètres de variante séparés par l’espace, un pour chaque paramètre.

### <a name="remarks"></a>Notes

Contrairement à la DISP_PROPERTY_EX macro, cette macro vous permet de spécifier une liste de paramètres pour la propriété. Ceci est utile pour la mise en œuvre de propriétés indexées ou paramétrées.

### <a name="example"></a>Exemple

Considérez la déclaration suivante d’obtenir et de définir les fonctions des membres qui permettent à l’utilisateur de demander une ligne et une colonne spécifiques lors de l’accès à la propriété :

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Ceux-ci correspondent à la macro DISP_PROPERTY_PARAM suivante dans la carte de répartition de contrôle :

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

À titre d’exemple, considérez les fonctions suivantes pour obtenir et définir les membres :

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Ceux-ci correspondent à la macro DISP_PROPERTY_PARAM suivante dans la carte de répartition de contrôle :

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

Fait d’une propriété existante la valeur par défaut d’un objet.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Nom de la classe.

*pszName (en)*<br/>
Nom externe de la propriété qui représente la "valeur" de l’objet.

### <a name="remarks"></a>Notes

L’utilisation d’une valeur par défaut peut simplifier la programmation de votre objet d’automatisation pour les applications Visual Basic.

La « valeur par défaut » de votre objet est la propriété qui est récupérée ou définie lorsqu’une référence à un objet ne spécifie pas une propriété ou une fonction de membre.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
