---
title: Déclenchement d'exceptions logicielles
ms.date: 11/04/2016
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
ms.openlocfilehash: 7c58ae2e2b6635345a162d11d2b75a9865d37751
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246404"
---
# <a name="raising-software-exceptions"></a>Déclenchement d'exceptions logicielles

Certaines des sources les plus courantes d'erreurs de programme ne sont pas marquées en tant qu'exceptions par le système. Par exemple, si vous essayez d'allouer un bloc de mémoire mais que la mémoire disponible est insuffisante, la fonction runtime ou API ne déclenche pas d'exception mais retourne un code d'erreur.

However, you can treat any condition as an exception by detecting that condition in your code and then reporting it by calling the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function. Le fait de marquer les erreurs de cette manière vous permet de tirer parti de la gestion structurée des exceptions pour tout type d'erreur d'exécution.

Pour utiliser la gestion structurée des exceptions avec des erreurs :

- Définissez votre propre code d'exception pour l'événement.

- Call `RaiseException` when you detect a problem.

- Utilisez les filtres de gestion des exceptions pour tester le code d'exception que vous avez défini.

The \<winerror.h> file shows the format for exception codes. Pour veiller à ne pas définir un code qui est en conflit avec un code d'exception existant, définissez le troisième bit le plus significatif à 1. Les quatre bits les plus significatifs doivent être définis comme indiqué dans le tableau suivant.

|Bits|Paramètre binaire recommandé|Description|
|----------|--------------------------------|-----------------|
|31-30|11|Ces deux bits décrivent l'état de base du code : 11 = erreur, 00 = succès, 01 = informatif, 10 = avertissement.|
|29|1|Bit client. Affectez-lui la valeur 1 pour les codes définis par l'utilisateur.|
|28|0|Bit réservé. (Laissez la valeur 0.)|

Vous pouvez définir les deux premiers bits à un paramètre autre 11 binaire, bien que le paramètre « erreur » soit appropriée pour la plupart des exceptions. Veillez à définir les bits 29 et 28 comme indiqué dans le tableau précédent.

The resulting error code should therefore have the highest four bits set to hexadecimal E. For example, the following definitions define exception codes that do not conflict with any Windows exception codes. (Toutefois, vous pouvez être amené à vérifier quels codes sont utilisés par les DLL tierces.)

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Après avoir défini un code d'exception, vous pouvez l'utiliser pour lever une exception. For example, the following code raises the `STATUS_INSUFFICIENT_MEM` exception in response to a memory allocation problem:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Si vous souhaitez déclencher simplement une exception, vous pouvez définir les trois derniers paramètres à 0. Les trois derniers paramètres sont utiles pour transmettre des informations supplémentaires et définir un indicateur qui empêche les gestionnaires de poursuivre l'exécution. See the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function in the Windows SDK for more information.

Dans vos filtres de gestion des exceptions, vous pouvez ensuite tester les codes que vous avez définis. Exemple :

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Voir aussi

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Structured exception handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)