#include <iostream>
#include <algorithm>

using namespace std;

int sequentialSearch(int arr[], int size, int target) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            return i;
        }
    }
    return -1;
}

int binarySearch(int arr[], int size, int target) {
    int left = 0, right = size - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}

int main() {
    const int MAX_SIZE = 100;
    int arr[MAX_SIZE], n, target;

    cout << "Enter number of elements (max " << MAX_SIZE << "): ";
    cin >> n;

    if (n > MAX_SIZE) {
        cout << "Error: Too many elements." << endl;
        return 1;
    }

    cout << "Enter elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    sort(arr, arr + n);
    cout << "Sorted elements: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    cout << "Enter target element: ";
    cin >> target;

    int seqResult = sequentialSearch(arr, n, target);
    if (seqResult != -1) {
        cout << "Sequential Search: Found at index " << seqResult << "." << endl;
    } else {
        cout << "Sequential Search: Not found." << endl;
    }

    int binResult = binarySearch(arr, n, target);
    if (binResult != -1) {
        cout << "Binary Search: Found at index " << binResult << "." << endl;
    } else {
        cout << "Binary Search: Not found." << endl;
    }

    return 0;
}
