function decodeValue(value, base) {
    return BigInt(parseInt(value, base));
}

function findConstant(points) {
    let result = BigInt(0);
    const size = points.length;

    for (let i = 0; i < size; i++) {
        const xi = points[i].x;
        const yi = points[i].y;

        let term = BigInt(1);
        for (let j = 0; j < size; j++) {
            if (i !== j) {
                const xj = points[j].x;
                term *= (-xj) / (xi - xj);
            }
        }

        result += yi * term;
    }

    return result;
}

function processInput(data) {
    const keys = data.keys;
    const k = keys.k;

    const points = [];

    for (const key in data) {
        if (key !== "keys") {
            const x = BigInt(key);
            const base = parseInt(data[key].base, 10);
            const value = data[key].value;

            const y = decodeValue(value, base);
            points.push({ x: x, y: y });
        }
    }

    return findConstant(points.slice(0, k));
}

function main() {
    const testCase1 = {
        "keys": { "n": 4, "k": 3 },
        "1": { "base": "10", "value": "4" },
        "2": { "base": "2", "value": "111" },
        "3": { "base": "10", "value": "12" },
        "6": { "base": "4", "value": "213" }
    };

    const testCase2 = {
        "keys": { "n": 10, "k": 7 },
        "1": { "base": "6", "value": "13444211440455345511" },
        "2": { "base": "15", "value": "aed7015a346d63" },
        "3": { "base": "15", "value": "6aeeb69631c227c" },
        "4": { "base": "16", "value": "e1b5e05623d881f" },
        "5": { "base": "8", "value": "316034514573652620673" },
        "6": { "base": "3", "value": "2122212201122002221120200210011020220200" },
        "7": { "base": "3", "value": "20120221122211000100210021102001201112121" },
        "8": { "base": "6", "value": "20220554335330240002224253" },
        "9": { "base": "12", "value": "45153788322a1255483" },
        "10": { "base": "7", "value": "1101613130313526312514143" }
    };

    const result1 = processInput(testCase1);
    const result2 = processInput(testCase2);

    console.log("Secret for TestCase 1:", result1.toString());
    console.log("Secret for TestCase 2:", result2.toString());
}

main();
