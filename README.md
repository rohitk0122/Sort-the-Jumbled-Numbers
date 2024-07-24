# Sort-the-Jumbled-Numbers
class Solution {
    public int[] sortJumbled(int[] mapping, int[] nums) {
         // Convert the nums array to a list for easier sorting
        List<Integer> numList=new ArrayList<>();
        for(int num : nums){
            numList.add(num);
        }

        // Define the custom comparator using the mapping
        Comparator<Integer> comparator =(a, b) ->{
            long mappedA = getMappedValue(mapping, a);
            long mappedB = getMappedValue(mapping, b);
            return Long.compare(mappedA, mappedB);
        };

        // Sort the list using the comparator
        Collections.sort(numList, comparator);

        // Convert the sorted list back to an array
        int[] sortedNums = new int[numList.size()];
        for(int i = 0; i < numList.size(); i++){
            sortedNums[i] = numList.get(i);
        }

        return sortedNums;
    }

    private static long getMappedValue(int[] mapping, int num){
        StringBuilder mappedValue = new StringBuilder();
        String numStr = String.valueOf(num);
        for (char digit : numStr.toCharArray()){
            mappedValue.append(mapping[digit - '0']);
        }
        return Long.parseLong(mappedValue.toString());
    }
}
