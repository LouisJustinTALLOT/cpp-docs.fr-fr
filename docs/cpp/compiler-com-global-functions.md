---
title: Fonctions globales COM du compilateur
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: c0a9c742ad9dcbb05ed2d78c954d5a597e3b57cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189778"
---
# <a name="compiler-com-global-functions"></a>Fonctions globales COM du compilateur

**Section spécifique de Microsoft**

Les routines suivantes sont disponibles :

|Fonction|Description|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Lève une [_com_error](../cpp/com-error-class.md) en réponse à un échec.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Remplace la fonction par défaut utilisée pour la gestion des erreurs COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convertit une valeur `BSTR` en `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convertit une valeur `char *` en `BSTR`.|

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes du support COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)
