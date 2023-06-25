<script>
    import { onMount } from "svelte";

    // Size of the game board
    const boardSize = 4;
    let score = 0;

    // Initialize the game board
    let board = Array(boardSize)
        .fill(null)
        .map(() => Array(boardSize).fill(0));

    // Add a random tile to the board
    function addRandomTile() {
        const emptyTiles = [];

        // Find all empty tiles
        for (let row = 0; row < boardSize; row++) {
            for (let col = 0; col < boardSize; col++) {
                if (board[row][col] === 0) {
                    emptyTiles.push({ row, col });
                }
            }
        }

        // Randomly select an empty tile
        const randomTile =
            emptyTiles[Math.floor(Math.random() * emptyTiles.length)];

        // Set the tile value to 2 or 4 (90% chance of 2, 10% chance of 4)
        board[randomTile.row][randomTile.col] = Math.random() < 0.9 ? 2 : 4;
    }

    // Handle keydown events for arrow keys
    function handleKeydown(event) {
        if (event.key === "ArrowUp") moveUp();
        if (event.key === "ArrowDown") moveDown();
        if (event.key === "ArrowLeft") moveLeft();
        if (event.key === "ArrowRight") moveRight();
    }

    // Move tiles up
    function moveUp() {
        for (let col = 0; col < boardSize; col++) {
            for (let row = 1; row < boardSize; row++) {
                if (board[row][col] !== 0) {
                    let currentRow = row;
                    while (
                        currentRow - 1 >= 0 &&
                        (board[currentRow - 1][col] === 0 ||
                            board[currentRow - 1][col] === board[row][col])
                    ) {
                        if (board[currentRow - 1][col] === 0) {
                            board[currentRow - 1][col] = board[currentRow][col];
                            board[currentRow][col] = 0;
                            currentRow--;
                        } else if (
                            board[currentRow - 1][col] === board[row][col]
                        ) {
                            board[currentRow - 1][col] *= 2;
                            score += board[currentRow - 1][col];
                            board[currentRow][col] = 0;
                            break;
                        }
                    }
                }
            }
        }

        for (let col = 0; col < boardSize; col++) {
            for (let row = 0; row < boardSize - 1; row++) {
                if (board[row][col] === 0) {
                    let currentRow = row;
                    while (
                        currentRow + 1 < boardSize &&
                        board[currentRow + 1][col] !== 0
                    ) {
                        board[currentRow][col] = board[currentRow + 1][col];
                        board[currentRow + 1][col] = 0;
                        currentRow++;
                    }
                }
            }
        }
        for (let col = 0; col < boardSize; col++) {
            for (let row = 1; row < boardSize; row++) {
                if (board[row][col] !== 0) {
                    let currentRow = row;
                    while (
                        currentRow - 1 >= 0 &&
                        (board[currentRow - 1][col] === 0 ||
                            board[currentRow - 1][col] === board[row][col])
                    ) {
                        if (board[currentRow - 1][col] === 0) {
                            board[currentRow - 1][col] = board[currentRow][col];
                            board[currentRow][col] = 0;
                            currentRow--;
                        } else if (
                            board[currentRow - 1][col] === board[row][col]
                        ) {
                            board[currentRow - 1][col] *= 2;
                            score += board[currentRow - 1][col];
                            board[currentRow][col] = 0;
                            break;
                        }
                    }
                }
            }
        }

        addRandomTile();
    }

    function moveDown() {
        for (let col = 0; col < boardSize; col++) {
            for (let row = boardSize - 2; row >= 0; row--) {
                if (board[row][col] !== 0) {
                    let currentRow = row;
                    while (
                        currentRow + 1 < boardSize &&
                        (board[currentRow + 1][col] === 0 ||
                            board[currentRow + 1][col] === board[row][col])
                    ) {
                        if (board[currentRow + 1][col] === 0) {
                            board[currentRow + 1][col] = board[currentRow][col];
                            board[currentRow][col] = 0;
                            currentRow++;
                        } else if (
                            board[currentRow + 1][col] === board[row][col]
                        ) {
                            board[currentRow + 1][col] *= 2;
                            score += board[currentRow + 1][col];
                            board[currentRow][col] = 0;
                            break;
                        }
                    }
                }
            }
        }
        for (let col = 0; col < boardSize; col++) {
            for (let row = boardSize - 1; row >= 0; row--) {
                if (board[row][col] === 0) {
                    let currentRow = row;
                    while (
                        currentRow - 1 >= 0 &&
                        board[currentRow - 1][col] !== 0
                    ) {
                        board[currentRow][col] = board[currentRow - 1][col];
                        board[currentRow - 1][col] = 0;
                        currentRow--;
                    }
                }
            }
        }
        for (let col = 0; col < boardSize; col++) {
            for (let row = boardSize - 2; row >= 0; row--) {
                if (board[row][col] !== 0) {
                    let currentRow = row;
                    while (
                        currentRow + 1 < boardSize &&
                        (board[currentRow + 1][col] === 0 ||
                            board[currentRow + 1][col] === board[row][col])
                    ) {
                        if (board[currentRow + 1][col] === 0) {
                            board[currentRow + 1][col] = board[currentRow][col];
                            board[currentRow][col] = 0;
                            currentRow++;
                        } else if (
                            board[currentRow + 1][col] === board[row][col]
                        ) {
                            board[currentRow + 1][col] *= 2;
                            score += board[currentRow + 1][col];
                            board[currentRow][col] = 0;
                            break;
                        }
                    }
                }
            }
        }

        addRandomTile();
    }

    function moveLeft() {
        for (let row = 0; row < boardSize; row++) {
            for (let col = 1; col < boardSize; col++) {
                if (board[row][col] !== 0) {
                    let currentCol = col;
                    while (
                        currentCol - 1 >= 0 &&
                        (board[row][currentCol - 1] === 0 ||
                            board[row][currentCol - 1] === board[row][col])
                    ) {
                        if (board[row][currentCol - 1] === 0) {
                            board[row][currentCol - 1] = board[row][currentCol];
                            board[row][currentCol] = 0;
                            currentCol--;
                        } else if (
                            board[row][currentCol - 1] === board[row][col]
                        ) {
                            board[row][currentCol - 1] *= 2;
                            score += board[row][currentCol - 1];
                            board[row][currentCol] = 0;
                            break;
                        }
                    }
                }
            }
        }

        for (let row = 0; row < boardSize; row++) {
            for (let col = 0; col < boardSize - 1; col++) {
                if (board[row][col] === 0) {
                    let currentCol = col;
                    while (
                        currentCol + 1 < boardSize &&
                        board[row][currentCol + 1] !== 0
                    ) {
                        board[row][currentCol] = board[row][currentCol + 1];
                        board[row][currentCol + 1] = 0;
                        currentCol++;
                    }
                }
            }
        }

        for (let row = 0; row < boardSize; row++) {
            for (let col = 1; col < boardSize; col++) {
                if (board[row][col] !== 0) {
                    let currentCol = col;
                    while (
                        currentCol - 1 >= 0 &&
                        (board[row][currentCol - 1] === 0 ||
                            board[row][currentCol - 1] === board[row][col])
                    ) {
                        if (board[row][currentCol - 1] === 0) {
                            board[row][currentCol - 1] = board[row][currentCol];
                            board[row][currentCol] = 0;
                            currentCol--;
                        } else if (
                            board[row][currentCol - 1] === board[row][col]
                        ) {
                            board[row][currentCol - 1] *= 2;
                            score += board[row][currentCol - 1];
                            board[row][currentCol] = 0;
                            break;
                        }
                    }
                }
            }
        }

        addRandomTile();
    }

    function moveRight() {
        for (let row = 0; row < boardSize; row++) {
            for (let col = boardSize - 2; col >= 0; col--) {
                if (board[row][col] !== 0) {
                    let currentCol = col;
                    while (
                        currentCol + 1 < boardSize &&
                        (board[row][currentCol + 1] === 0 ||
                            board[row][currentCol + 1] === board[row][col])
                    ) {
                        if (board[row][currentCol + 1] === 0) {
                            board[row][currentCol + 1] = board[row][currentCol];
                            board[row][currentCol] = 0;
                            currentCol++;
                        } else if (
                            board[row][currentCol + 1] === board[row][col]
                        ) {
                            board[row][currentCol + 1] *= 2;
                            score += board[row][currentCol + 1];
                            board[row][currentCol] = 0;
                            break;
                        }
                    }
                }
            }
        }

        for (let row = 0; row < boardSize; row++) {
            for (let col = boardSize - 1; col >= 0; col--) {
                if (board[row][col] === 0) {
                    let currentCol = col;
                    while (
                        currentCol - 1 >= 0 &&
                        board[row][currentCol - 1] !== 0
                    ) {
                        board[row][currentCol] = board[row][currentCol - 1];
                        board[row][currentCol - 1] = 0;
                        currentCol--;
                    }
                }
            }
        }

        for (let row = 0; row < boardSize; row++) {
            for (let col = boardSize - 2; col >= 0; col--) {
                if (board[row][col] !== 0) {
                    let currentCol = col;
                    while (
                        currentCol + 1 < boardSize &&
                        (board[row][currentCol + 1] === 0 ||
                            board[row][currentCol + 1] === board[row][col])
                    ) {
                        if (board[row][currentCol + 1] === 0) {
                            board[row][currentCol + 1] = board[row][currentCol];
                            board[row][currentCol] = 0;
                            currentCol++;
                        } else if (
                            board[row][currentCol + 1] === board[row][col]
                        ) {
                            board[row][currentCol + 1] *= 2;
                            score += board[row][currentCol + 1];
                            board[row][currentCol] = 0;
                            break;
                        }
                    }
                }
            }
        }

        addRandomTile();
    }

    // Assign colors to tile values
function tileColor(value) {
    switch (value) {
  case 2:
    return 'background-color: #fff9cc; color: #776e65; animation: moveTile 0.2s;';
  case 4:
    return 'background-color: #ffed99; color: #776e65; animation: moveTile 0.2s;';
  case 8:
    return 'background-color: #ffdf66; color: #f9f6f2; animation: moveTile 0.2s;';
  case 16:
    return 'background-color: #ffcf33; color: #f9f6f2; animation: moveTile 0.2s;';
  case 32:
    return 'background-color: #ffc400; color: #f9f6f2; animation: moveTile 0.2s;';
  case 64:
    return 'background-color: #ffb100; color: #f9f6f2; animation: moveTile 0.2s;';
  case 128:
    return 'background-color: #ffa000; color: #f9f6f2; animation: moveTile 0.2s;';
  case 256:
    return 'background-color: #ff9000; color: #f9f6f2; animation: moveTile 0.2s;';
  case 512:
    return 'background-color: #ff8000; color: #f9f6f2; animation: moveTile 0.2s;';
  case 1024:
    return 'background-color: #ff7000; color: #f9f6f2; animation: moveTile 0.2s;';
  case 2048:
    return 'background-color: #ff6000; color: #f9f6f2; animation: moveTile 0.2s;';
  default:
    return 'background-color: #ccc0b3; color: #776e65;';
}

}


    // Initialize the game
    onMount(() => {
        addRandomTile();
        addRandomTile();
    });

    function thaiNumber(txt) {
        txt = txt.toString();

        txt = txt.replace('0', '๐')
        txt = txt.replace('1', '๑')
        txt = txt.replace('2', '๒')
        txt = txt.replace('3', '๓')
        txt = txt.replace('4', '๔')
        txt = txt.replace('5', '๕')
        txt = txt.replace('6', '๖')
        txt = txt.replace('7', '๗')
        txt = txt.replace('8', '๘')
        txt = txt.replace('9', '๙')
        
        return txt;
    }
</script>

<div on:keydown={handleKeydown} tabindex="0">
    <h3>คะแนน: {thaiNumber(thaiNumber(score))} </h3>
    <div class="board">
        {#each board as row, rowIndex}
            <div style="display: flex;">
                {#each row as tile, colIndex}
                    {#if tile !== 0}
                        <div class="tile" style="margin: 5px; {tileColor(tile)}">{thaiNumber(tile)}</div>
                    {:else}
                        <div class="tile" style="margin: 5px;" />
                    {/if}
                {/each}
            </div>
        {/each}
    </div>
</div>

<style>
    /* Style the game board */
    .board {
        display: grid;
        grid-template-columns: repeat("${boardSize}", 1fr);
        grid-template-rows: repeat("${boardSize}", 1fr);
        width: 400px;
        height: 400px;
        background-color: #bbada0;
    }

    /* Style the individual tiles */
    .tile {
        width: 90px;
        height: 90px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 32px;
        font-weight: bold;
        background-color: #ccc0b3;
        border-radius: 5px;
        color: #776e65;
    }

    .board {
        gap: 0;
    }

    @keyframes moveTile {
  0% {
    transform: scale(0.8);
  }
  100% {
    transform: scale(1);
  }
}

</style>
