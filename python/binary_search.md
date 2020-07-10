<h1>Binary Search algorithm</h1>

<p>
1 - Let min = 0 and max = n-1.<br />
2 - If max < min, then stop: target is not present in array. Return -1.<br />
3 - Compute guess as the average of max and min, rounded down (so that it is an integer).<br />
4 - If array[guess] equals target, then stop. You found it! Return guess.<br />
5 - If the guess was too low, that is, array[guess] < target, then set min = guess + 1.<br />
6 - Otherwise, the guess was too high. Set max = guess - 1.<br />
7 - Go back to step 2.
</p>

    def binary_search(sorted_array, target):
        min = 0
        max = len(sorted_array) - 1
        while min <= max:
            midpoint = min + (max - min) // 2
            guess = sorted_array[midpoint]
            if guess == target:
                return midpoint
            elif guess > target:
                max = midpoint - 1
            else:
                min = midpoint + 1
        return None

    sorted_array = [5, 10, 15, 20, 25, 30, 35, 40, 45, 50]
    print(binary_search(sorted_array, 30))