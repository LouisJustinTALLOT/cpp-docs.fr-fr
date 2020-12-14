---
description: 'En savoir plus sur : Comment : appeler des DLL natives à partir de code managé à l’aide de PInvoke'
title: "Comment : appeler des DLL natives à partir du code managé à l'aide de PInvoke"
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: 915601aa813f1c5c14977c1492d6c675125c47be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335394"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Comment : appeler des DLL natives à partir du code managé à l'aide de PInvoke

Les fonctions implémentées dans des dll non managées peuvent être appelées à partir du code managé à l’aide de la fonctionnalité d’appel de code non managé (P/Invoke). Si le code source de la DLL n’est pas disponible, P/Invoke est la seule option pour l’interopérabilité. Toutefois, contrairement à d’autres langages .NET, Visual C++ fournit une alternative à P/Invoke. Pour plus d’informations, consultez [utilisation de l’interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Exemple

L’exemple de code suivant utilise la fonction Win32 [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics) pour récupérer la résolution actuelle de l’écran en pixels.

Pour les fonctions qui utilisent uniquement des types intrinsèques comme arguments et des valeurs de retour, aucun travail supplémentaire n’est nécessaire. D’autres types de données, tels que les pointeurs de fonction, les tableaux et les structures, requièrent des attributs supplémentaires pour garantir un marshaling de données correct.

Bien qu’il ne soit pas obligatoire, il est conseillé de faire en sorte que les déclarations P/Invoke soient des membres statiques d’une classe value afin qu’ils n’existent pas dans l’espace de noms global, comme illustré dans cet exemple.

```cpp
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
