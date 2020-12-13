---
description: 'En savoir plus sur : fonctions globales COM du compilateur'
title: Fonctions globales COM du compilateur
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 74449d26-50a2-47c7-b175-7cf2cf83533e
ms.openlocfilehash: d678372bdc5703aa05fdf093b84075b7286c4b9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335552"
---
# <a name="compiler-com-global-functions"></a>Fonctions globales COM du compilateur

**Spécifique à Microsoft**

Les routines suivantes sont disponibles :

|Fonction|Description|
|--------------|-----------------|
|[_com_raise_error](../cpp/com-raise-error.md)|Lève une [_com_error](../cpp/com-error-class.md) en réponse à un échec.|
|[_set_com_error_handler](../cpp/set-com-error-handler.md)|Remplace la fonction par défaut utilisée pour la gestion des erreurs COM.|
|[ConvertBSTRToString](../cpp/convertbstrtostring.md)|Convertit une valeur `BSTR` en `char *`.|
|[ConvertStringToBSTR](../cpp/convertstringtobstr.md)|Convertit une valeur `char *` en `BSTR`.|

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classes de prise en charge COM du compilateur](../cpp/compiler-com-support-classes.md)<br/>
[Prise en charge COM du compilateur](../cpp/compiler-com-support.md)
