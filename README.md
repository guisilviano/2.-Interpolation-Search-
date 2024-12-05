def interpolation_search(arr, target):
    """
    Realiza uma busca por interpolação em uma lista ordenada.

    :param arr: Lista ordenada de elementos.
    :param target: Elemento a ser encontrado.
    :return: Índice do elemento, ou -1 se não encontrado.
    """
    low = 0
    high = len(arr) - 1

    while low <= high and target >= arr[low] and target <= arr[high]:
        # Evita divisão por zero
        if low == high:
            if arr[low] == target:
                return low
            return -1

        # Fórmula de interpolação para estimar a posição
        pos = low + ((high - low) // (arr[high] - arr[low]) * (target - arr[low]))

        # Verifica se o elemento está na posição calculada
        if arr[pos] == target:
            return pos

        # Ajusta os limites de busca
        if arr[pos] < target:
            low = pos + 1
        else:
            high = pos - 1

    return -1


# Testes
if __name__ == "__main__":
    data = [10, 20, 30, 40, 50, 60, 70, 80, 90]
    target = 70
    result = interpolation_search(data, target)
    if result != -1:
        print(f"Elemento {target} encontrado no índice {result}.")
    else:
        print(f"Elemento {target} não encontrado.")
